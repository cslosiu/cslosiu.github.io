# UI Map

```
WorkspaceList
  └─ WorkspaceDetail
       ├─ Enumerables / Classes / Instances
       ├─ Views
       │    ├─ ViewList (create: one+ Classes + columns + optional group-by/aggregates + filters)
       │    ├─ ViewRuntime (join/Cartesian, Class › Field columns, optional GROUP BY + aggregates, sort, class drill-down)
       │    └─ RecordDetail (all properties; class fields drill further)
       └─ Forms
            ├─ FormList (create: name + Class; rename / delete)
            └─ FormEntry (typed editors; Submit saves instance and clears for next)
```

## View create

1. Name + one or more Classes.
2. Choose output columns from all selected classes (`Class › Field`; default: all).
3. Optional: group by those columns; aggregations may use int/float from any selected class.
4. Optional filters (AND/OR) on fields from any selected class.

## View runtime

1. Join selected classes on Class-reference associations (INNER JOIN); unconnected classes use Cartesian product.
2. Apply filters on joined rows; optionally GROUP BY output columns and compute aggregates.
3. Tap header to sort.
4. Tap Class value → RecordDetail; Class fields there continue to drill down.

## Form create

1. Name + Class.
2. Opening the form shows all class properties with typed editors (pickers for enum/class, constrained number/date/color).
3. **Submit** saves a new instance and resets the form for another entry. Leaving without Submit discards the draft.

## Empty workspace

**Generate Sample** seeds an Oracle HR–inspired schema (Region, Country, Location, Job, Department, Employee, Job History), demo Views (including joins / group-by), and a Form per class.
