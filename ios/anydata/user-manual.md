# AnyData User Manual

**AnyData - Design your database** is a local custom-database app for iPhone and iPad.  
You can create multiple **Workspaces**, define **Enumerables** and **Classes**, enter data with **Instances** / **Forms**, explore with **Views** (filters, joins, and aggregations), inspect structure in the **ER Diagram**, and export SQL or CSV.

Data is stored on device (SwiftData). **No account** is required, and the app does not sync to the cloud automatically.

> UI labels (for example `Workspaces`, `Generate Sample`, `Submit`) match the English interface.

---

## Contents

1. [Quick start](#1-quick-start)
2. [Workspaces](#2-workspaces)
3. [Enumerables](#3-enumerables)
4. [Classes and Properties](#4-classes-and-properties)
5. [Instances](#5-instances)
6. [Forms](#6-forms)
7. [Views](#7-views)
8. [ER Diagram](#8-er-diagram)
9. [Export](#9-export)
10. [Generate Sample](#10-generate-sample)
11. [Capabilities and limits](#11-capabilities-and-limits)
12. [Glossary](#12-glossary)

---

## 1. Quick start

### Suggested flow

1. Open the app → create a **Workspace**.  
2. (Optional) In an empty Workspace, tap **Generate Sample** for demo schema and data.  
3. Or build yourself: **Enumerables** → **Classes / Properties** → **Instances** or **Forms** → **Views**.  
4. Use **ER Diagram** to check relationships; export from the **⋯** menu when needed.

### Navigation

```
Workspaces
  └─ <Workspace>
       ├─ Enumerables
       ├─ Classes → Properties / Instances
       ├─ Views
       ├─ Forms
       ├─ Generate Sample (empty Workspace only)
       └─ ⋯ menu → Export… / ER Diagram
```

---

## 2. Workspaces

A **Workspace** is an independent data space. Enums, Classes, Instances, Views, and Forms belong to one Workspace and are not shared across Workspaces.

| Action | How |
|--------|-----|
| Add | On the `Workspaces` list, tap **+** |
| Rename | Use the list edit / menu actions (follow the UI) |
| Delete | Swipe to delete or use the menu (removes all data inside) |
| Open | Tap the Workspace name |

---

## 3. Enumerables

An **Enumerable** is a fixed set of allowed values (for example status codes or country codes) that Class properties can use.

| Action | Notes |
|--------|--------|
| Manage Enumerables | Create, open, and manage all enums |
| Add value | Add a case on the enum editor |
| Delete value | Supported |
| Uniqueness | Duplicate value names are **not** allowed (compared after trimming) |

---

## 4. Classes and Properties

A **Class** is like a table; a **Property** is a field. All properties are **optional**.

### Property types

| Type (UI) | Description |
|-----------|-------------|
| **String** | Text |
| **Date/Time** | Date and time |
| **Date** | Date only |
| **Time** | Time only |
| **Integer** | Whole number |
| **Float** | Decimal number |
| **Color** | System ColorPicker; can be cleared |
| **Enumerable** | Bound to an Enumerable |
| **Class** | Reference to an Instance of another Class (foreign-key style) |

### Common steps

1. **Manage Classes** → add a Class.  
2. Open the Class → edit **Properties** (name, type, Enum / Class binding).  
3. For relationships, add a **Class**-typed property and choose the target Class.

---

## 5. Instances

An **Instance** is one row of data for a Class.

1. Open a Class → **Instances**.  
2. Tap **+** to add, or tap a row to edit.  
3. Use the control that matches each property type (keyboard, DatePicker, Picker, ColorPicker, and so on).

Delete: swipe to delete in the list (follow the UI).

> **Record Detail** opened by drilling down from a View is mainly for viewing. For full editing, use Class → Instances.

---

## 6. Forms

A **Form** is a data-entry UI bound to a single Class, suited to entering many records in a row.

### Create a Form

1. Workspace → **Forms** → **Manage Forms** → **+**.  
2. Enter a name (defaults to the selected Class name).  
3. Choose a **Class** → **Create**.

### Fill in data

1. Open the Form from the Forms list or Manage Forms.  
2. Fill the properties.  
3. Tap **Submit**: saves a new Instance and clears the form for the next record.  
4. **Leaving without Submit** discards the current draft.

You can rename or delete a Form without affecting Instances already saved.

---

## 7. Views

A **View** queries and browses data. It supports multiple Classes, filters, and group-by aggregations.

### Create a View

1. **Manage Views** → **+** (**New View**).  
2. Enter a name.  
3. **Select one or more Classes**.  
4. Choose **Output Columns** (shown as `Class › Field`; if none are selected, all columns are included).  
5. (Optional) Turn on **Group by output columns** and add aggregations:  
   - **Count** (no numeric field required)  
   - **Sum / Average / Min / Max / Median** (pick an Integer or Float field from a selected Class)  
6. (Optional) **Filters**: AND / OR with typed comparators; fields may come from any selected Class.  
7. **Create**.

> After creation you **cannot change the Classes**; everything else is editable.

### Edit an existing View

In **Manage Views**, tap **⋯** → **Edit…** to change:

- Name  
- Output columns  
- Group by / aggregations  
- Filters  

### Run a View

- Tap the View name to open the table.  
- Multi-class Views **with Class references**: related with INNER JOIN.  
- **Unrelated** Classes: Cartesian product.  
- Apply Filters → (optional) GROUP BY and aggregations.  
- Tap a column header to sort.  
- Tap an accent-colored **Class** value to open **Record Detail**.

### List subtitles

Workspace and Manage Views lists show Classes, a **filter summary**, and group-by / aggregation hints in secondary text.

---

## 8. ER Diagram

1. Workspace → **⋯** → **ER Diagram**.  
2. **Class** and **Enumerable** use different styles; links use crow’s foot notation.  
3. Gestures: drag tables, pinch to zoom, drag the background to pan.  
4. **Auto Layout**: lays out by screen width (about 3 columns max), reduces overlap and crossings, favors vertical scrolling.  
5. **Reset** restores the default grid; **Recenter** resets pan.  
6. **Export** PNG or PDF via the system share sheet.

---

## 9. Export

From the Workspace **⋯** menu:

| Command | Contents |
|---------|----------|
| **Export SQL DDL** | ANSI-style `CREATE TABLE` (with `id` primary key), foreign keys, enum lookup tables, `CREATE VIEW` |
| **Export Data SQL** | `INSERT` statements |
| **Export Data CSV** | Per-table CSV files packaged as a **zip**, shared via the system share sheet |

Notes:

- Each Class / Enum maps to a table; rows use the Instance / case **UUID** as `id` (primary key).  
- Class / Enum reference fields export as `CHAR(36)` suitable for foreign keys.  
- App properties are optional, so ordinary DDL columns are **NULL**; `id` is **NOT NULL**.  
- **Median** has no standard core ANSI function; DDL Views use a comment placeholder.  
- Files are written under App Caches, then the system share sheet opens.

---

## 10. Generate Sample

When a Workspace is **completely empty** (no Enum / Class / View / Form), the toolbar shows **Generate Sample**.

It creates an Oracle **HR**-inspired demo:

- Classes: Region, Country, Location, Job, Department, Employee, Job History  
- Sample Instances (including org hierarchy)  
- Sample Views (JOIN, filters, GROUP BY)  
- One Form per Class (same name as the Class)  

See [sample data notes](user-guide-sample-data.md).

---

## 11. Capabilities and limits

### Supported

- Multiple on-device Workspaces  
- Nine property types and Class references  
- Forms for continuous data entry  
- Multi-class Views, Filters, GROUP BY, and aggregations  
- ER Diagram with PNG / PDF export  
- SQL DDL / INSERT / CSV export  

### Not supported / caveats

- Required-field constraints (all properties are optional)  
- Cross-Workspace references  
- Cloud sync / accounts  
- Changing selected Classes after a View is created  
- Full editing inside Record Detail (use Instances)  
- Exported SQL may need tweaks for your target database (ANSI-oriented; not guaranteed to run on every engine as-is)

---

## 12. Glossary

| Term | Meaning |
|------|---------|
| Workspace | Independent database space |
| Enumerable | Enum / pick list |
| Class | Data type / table |
| Property | Field |
| Instance | One record |
| Form | Class-bound entry form |
| View | Query / browse definition |
| Filter | Filter condition |
| Group by | Grouping |
| Aggregation | Count / Sum / Avg / Min / Max / Median |
| ER Diagram | Entity-relationship diagram |
| Generate Sample | Create demo data |

---

## Related docs

- [App Store submission copy](app-store-submission.md)  
- [Sample data notes](user-guide-sample-data.md)  
- [Data model (developers)](data-model.md)  
- [UI map (developers)](ui-map.md)  

---

*This manual matches the feature set that includes Forms, multi-class Views, ER Auto Layout, and SQL / CSV export.*
