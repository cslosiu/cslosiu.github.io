---
layout: post
title: Read google firestore data to SwiftUI list view
category: IT
---

This should be a common problem but it's hard to find correct and up-to-date reference. AI does not give anything good. Anyway here is the working way.

The key things are:

- Define a struct to model the data object we care about. 
- Then to have a class (not struct) subclassing ObservableObject with a @Published array of that model. The class has a method to read the data and decode it to the model and map the returned documents to the array.
- Sort it if necessary.
- Pass the array to a List view.

So here is:

```swift
import SwiftUI
import Foundation
import Firebase
import FirebaseFirestore


struct Seat: Identifiable, Codable {
    let id: String
    let enabled: Bool
    let number: String
    let occupied: Bool
    let table: String
}


class SeatViewModel: ObservableObject {
    @Published var seats: [Seat] = []
    private var db = Firestore.firestore()

    func fetchSeats() {
        db.collection("seat").getDocuments { (querySnapshot, error) in
            if let error = error {
                print("Error getting documents: \(error)")
            } else {
                self.seats = querySnapshot?.documents.map { queryDocumentSnapshot -> Seat in
                      let data = queryDocumentSnapshot.data()
                      let number = data["number"] as? String ?? ""
                      let table = data["table"] as? String ?? ""
                      let enabled = data["enabled"] as? Bool ?? true
                      let occupied = data["occupied"] as? Bool ?? false
               
                    return Seat(id: queryDocumentSnapshot.documentID,
                                enabled: enabled, number: number, occupied: occupied, table: table)
                } ?? []
                
                self.seats = self.seats.sorted { seat1, seat2 in
                    return seat1.table + seat1.number < seat2.table + seat2.number
                }
            }
        }
    }
}


struct SeatListView: View {
    @StateObject private var viewModel = SeatViewModel()

    var body: some View {
        List(viewModel.seats) { seat in
            HStack {
                if seat.occupied {
                    Image(systemName: "circle.fill")
                        .foregroundColor(.red)
                }
                else {
                    Image(systemName: "circle")
                        .foregroundColor(.green)
                }
                VStack(alignment: .leading) {
                    Text(seat.table + seat.number)
                        .font(.headline)
                    Text(seat.occupied ? "Occupied" : "Available")
                        .font(.subheadline)
                }
            }
        }
        .navigationTitle("Seats")
        .onAppear {
            viewModel.fetchSeats()
        }
    }
}
```
