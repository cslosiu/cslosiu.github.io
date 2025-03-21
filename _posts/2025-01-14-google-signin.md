---
layout: post
title: Use google sign in in Swift (iOS) with Firebase
category: IT
---

The documentation on Google is fucking out of date. 

Finally we find here:

https://medium.com/@matteocuzzolin/google-sign-in-with-firebase-in-swiftui-app-c8dc7b7ed4f9

To keep a copy, below I copy the code part, which is the out-dated part of Google's guide.

The App class:

```swift
import SwiftUI
import SwiftData
import FirebaseCore
import Firebase
import FirebaseAuth
import GoogleSignIn

@main
struct dineinposApp: App {
    var sharedModelContainer: ModelContainer = {
        let schema = Schema([
            Item.self,
        ])
        let modelConfiguration = ModelConfiguration(schema: schema, isStoredInMemoryOnly: false)

        do {
            return try ModelContainer(for: schema, configurations: [modelConfiguration])
        } catch {
            fatalError("Could not create ModelContainer: \(error)")
        }
    }()
    
    init() {
        // Firebase initialization
        FirebaseApp.configure()
    }

    var body: some Scene {
        WindowGroup {
            ContentView().onOpenURL { url in
                //Handle Google Oauth URL
                GIDSignIn.sharedInstance.handle(url)
            }
        }
        .modelContainer(sharedModelContainer)
    }
}
```

The main logic that google wants us to glue things up:

```swift

import Foundation
import Firebase
import FirebaseAuth
import GoogleSignIn

struct Authentication {
    @MainActor
    func googleOauth() async throws {
        // google sign in
        guard let clientID = FirebaseApp.app()?.options.clientID else {
            fatalError("no firbase clientID found")
        }

        // Create Google Sign In configuration object.
        let config = GIDConfiguration(clientID: clientID)
        GIDSignIn.sharedInstance.configuration = config
        
        //get rootView
        let scene = UIApplication.shared.connectedScenes.first as? UIWindowScene
        guard let rootViewController = scene?.windows.first?.rootViewController
        else {
            fatalError("There is no root view controller!")
        }
        
        //google sign in authentication response
        let result = try await GIDSignIn.sharedInstance.signIn(
            withPresenting: rootViewController
        )
        let user = result.user
        guard let idToken = user.idToken?.tokenString else {
            throw AuthenticationError.runtimeError("Unexpected error occurred, please retry")
        }
        
        //Firebase auth
        let credential = GoogleAuthProvider.credential(
            withIDToken: idToken, accessToken: user.accessToken.tokenString
        )
        try await Auth.auth().signIn(with: credential)
    }
    
    func logout() async throws {
        GIDSignIn.sharedInstance.signOut()
        try Auth.auth().signOut()
    }
}

enum AuthenticationError: Error {
    case runtimeError(String)
}
```

The content view (entry view) and Home view (success) or Login view (the login button)

```swift
import Firebase
import FirebaseCore
import FirebaseAuth
import GoogleSignIn


struct ContentView: View {
    @State private var userLoggedIn = (Auth.auth().currentUser != nil)

    @Environment(\.modelContext) private var modelContext
    @Query private var items: [Item]
    
    var body: some View {
        VStack {
            if userLoggedIn {
                Home()
            } else {
                Login()
            }
        }.onAppear{
            //Firebase state change listeneer
            Auth.auth().addStateDidChangeListener{ auth, user in
                if (user != nil) {
                    userLoggedIn = true
                } else {
                    userLoggedIn = false
                }
            }
        }
    }
    
    var body1: some View {
        TabView {
            FirstView()
                .tabItem {
                    Label("Order", systemImage: "1.circle")
                }
        }
        .tabViewStyle(SidebarAdaptableTabViewStyle())
    }
    
}


struct Home: View {
    @State private var err : String = ""
    
    var body: some View {
        HStack {
            Image(systemName: "hand.wave.fill")
            Text(
                "Hello " +
                (Auth.auth().currentUser!.displayName ?? "Username not found")
            )
        }
        Button{
            Task {
                do {
                    try await Authentication().logout()
                } catch let e {
                    err = e.localizedDescription
                }
            }
        }label: {
            Text("Log Out").padding(8)
        }.buttonStyle(.borderedProminent)
        
        Text(err).foregroundColor(.red).font(.caption)
    }
}


struct Login: View {
    @State private var err : String = ""
    
    var body: some View {
        Text("Login")
        Button{
            Task {
                do {
                    try await Authentication().googleOauth()
                } catch AuthenticationError.runtimeError(let errorMessage) {
                    err = errorMessage
                }
            }
        }label: {
            HStack {
                Image(systemName: "person.badge.key.fill")
                Text("Sign in with Google")
            }.padding(8)
        }.buttonStyle(.borderedProminent)
        
        Text(err).foregroundColor(.red).font(.caption)
    }
}
```
