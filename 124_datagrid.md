# Enums: DataGrid

### DataGridFilterMethod

- Contains search for any occurrence (default)
- StartsWith search only the beginning
- EndsWith search only the ending
- Equals search must match the entire value
- NotEquals opposite of Equals

### DataGridSortMode

- Single The data grid can only be sorted by one column at a time.
- Multiple The data grid can sorted by multiple columns.

### DataGridSelectionMode

- Single The data grid only supports a row selected at a time.
- Multiple The data grid enables multiple rows to be selected.

### DataGridCommandMode

- Default Default state which means that both defined commands and button row will render.
- Commands Only defined commands will render.
- ButtonRow Only button row will render.

### DataGridPagerPosition

- Top Positions the pagination above the table.
- Bottom Positions the pagination below the table.
- TopAndBottom Positions the pagination on above and below the table.

### DataGridAggregateRowPosition

- Top Positions the aggregate row above the table data as the last table header row.
- Bottom Positions the aggregate row in the footer of the table.
- TopAndBottom Positions the aggregate row with both Top and Bottom definition.

### SortDirection

Specifies the direction of a sort operation.

- None No sorting will be applied.
- Ascending Sorts in ascending order.
- Descending Sorts in descending order.

### DataGridSelectReason

Defines the Select Reason of the DataGrid Selection.

- RowClick Row has been clicked.
- MultiSelectClick Multi select has been triggered.
- MultiSelectAll Multi select all has been triggered.

### DetailRowTriggerType

Defines the DetailRowTriggerType of the DataGrid's DetailRow.

- Manual Trigger is manually controlled by invoking the Datagrid's ToggleDetailRow
- RowClick Triggers on row click.

### PagerElementPosition

Sets a Pager Element's position.

- Default Positions the element at the default position. If both ButtonRowPosition and PaginationPosition are set to default. Whether ButtonRow is shown or not will make it so the Pagination is positioned accordingly.
- Start Positions the element at the start.
- Center Positions the element at the center.
- End Positions the element at the end.

###### On this page

#### 

## 