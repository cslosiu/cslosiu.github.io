# tasking

**tasking** is a local-first project and task manager for iOS. It is built around **task dependencies**: you define which tasks must be completed before others can start, and the app enforces those rules automatically.

Use it when a simple checklist is not enough, but you do not need the complexity of enterprise project software.

---

## What makes tasking different

Most to-do apps treat every task as independent. **tasking** models real workflows:

- If **Task B** depends on **Task A**, then **B cannot start until A is done**.
- When prerequisites are incomplete, dependent tasks are marked **Blocked**.
- The app prevents **circular dependencies** (for example, A → B → A).
- A **dependency graph** shows how tasks connect visually.

All data is stored on your device. No account or sign-in is required.

---

## Main concepts

### Projects

A **project** is a container for related work. Each project can include:

| Field | Description |
|-------|-------------|
| Name | Project title |
| Client | Client name and remarks |
| Due date | Optional project deadline |
| Staff | Team members who can be assigned to tasks |
| Milestones | Named dates on the project timeline (cannot be after the project due date) |
| Remarks | General project notes |

### Tasks

A **task** belongs to one project and can have:

| Field | Description |
|-------|-------------|
| Title | Task name |
| Notes | Multi-line description |
| Priority | None, Low, High, or Urgent |
| Due date | Optional date-only deadline |
| Status | New, In Progress, Done, or Blocked |
| Assignees | One or more staff members from the project |
| Prerequisites | Other tasks that must be completed first |

### Dependencies

A dependency means: **prerequisite → dependent**.

- The **prerequisite** must be **Done** before the **dependent** can start.
- A task can have **multiple** prerequisites.
- You cannot create a dependency on the same task, a duplicate link, or a cycle.

---

## Getting started

### 1. Create a project

1. Open the app. You land on the **Projects** list.
2. Tap **+** in the top-right corner.
3. Enter a project name (required) and optional details.
4. Tap **Create**.

### 2. Add staff (optional but recommended)

Staff members are needed before you can assign tasks.

1. Open the project.
2. Tap the **info** button or choose **Project Details** from the menu (⋯).
3. In **Staff**, type a name and tap **Add**.
4. Repeat for each team member.

### 3. Create tasks

1. Inside a project, tap **+** to add a task.
2. Enter a title and tap **Create**.
3. Tap the task to open its detail screen and add notes, priority, due date, and assignees.

### 4. Set up dependencies

1. Open a task.
2. In **Prerequisites**, tap **Edit Dependencies**.
3. Search for a task and tap **Add** to make it a prerequisite.
4. Tap **Done**.

**Example:** For tasks *Book flights* and *Book hotel*:

- Add *Book flights* as a prerequisite of *Book hotel* only if flights must be booked first.
- Direction matters: prerequisite → dependent.

### 5. Work through tasks

Open a task and use the **Actions** section:

| Status | Available actions |
|--------|-------------------|
| **New** or **Blocked** | **Start Task** (only if all prerequisites are Done) |
| **In Progress** | **Complete Task** |
| **Done** | **Revert to In Progress** |

If prerequisites are not finished, the app shows a message listing which tasks must be completed first instead of a Start button.

When you complete a prerequisite, dependent tasks are re-evaluated. If all prerequisites are done, a **Blocked** task becomes **New** and can be started.

---

## Task list tools

Inside a project, use the **menu** (⋯) in the top-right:

### Filter

| Option | Shows |
|--------|-------|
| **All Tasks** | Every task in the project |
| **Available** | Tasks that can be started now (New, or Blocked with all prerequisites done) |
| **Blocked** | Tasks waiting on incomplete prerequisites |

### Sort

| Option | Order |
|--------|-------|
| **Created Date** | Oldest or newest first (by creation time) |
| **Due Date** | By due date |
| **Priority** | By priority level |

### View Task Dependency

Opens an interactive **dependency graph**:

- Each task appears as a node.
- Arrows point from prerequisite to dependent.
- Drag nodes to rearrange the layout.

On iPad and other large screens, sheets such as the graph and project details open full screen for easier editing.

### Create Sample Tasks

When a project has **no tasks**, the menu offers **Create Sample Tasks**. This adds a realistic overseas business trip workflow with staff, milestones, assignees, and dependencies so you can explore the app quickly.

---

## Project details

Open **Project Details** from the info button or the menu to edit:

- Project name and remarks
- Client name and client remarks
- Project due date
- Staff list (swipe to delete)
- Milestones (name + date; milestone dates cannot exceed the project due date)

Changes are saved as you edit.

---

## Task statuses explained

| Status | Meaning |
|--------|-------|
| **New** | Ready to start (all prerequisites complete, or no prerequisites) |
| **In Progress** | Work has started |
| **Done** | Task is finished |
| **Blocked** | Has prerequisites that are not yet Done |

Status is managed by the app based on your actions and dependency rules. You cannot change status manually from the picker; use **Start**, **Complete**, or **Revert** instead.

---

## Priority levels

| Level | Color (in list) |
|-------|-----------------|
| None | Default |
| Low | Blue |
| High | Orange |
| Urgent | Red |

Priority affects sort order and how tasks appear in the list. It does not change dependency rules.

---

## Deleting items

- **Projects:** Swipe left on the Projects list, then confirm deletion. This removes the project and all its tasks.
- **Tasks:** Swipe left in the task list, or use **Delete Task** on the task detail screen.

Deletion cannot be undone.

---

## Tips

1. **Add staff before assigning tasks** — assignees are chosen from the project staff list.
2. **Set the project due date first** — milestone dates must fall on or before that date.
3. **Use the graph** — when dependencies get complex, the graph makes the flow easier to understand.
4. **Try the sample project** — use **Create Sample Tasks** on an empty project to see dependencies in action.
5. **Filter by Blocked** — quickly find what is waiting on other work.

---

## Privacy and data

- All projects and tasks are stored **locally on your device** using SwiftData.
- No cloud sync or account is required in the current version.
- For privacy policy and support, visit:
  - Privacy: https://losiu.com/ios/privacy
  - Support: https://losiu.com/ios/support

---

## Requirements

- iOS 17.0 or later
- iPhone and iPad supported
- Light Mode and Dark Mode follow your system appearance setting
