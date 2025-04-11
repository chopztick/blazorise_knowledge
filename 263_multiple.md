# Blazorise DataGrid: Multiple Selection

The DataGrid allows you to select rows with the click of a mouse.

### Multiple Selection

Set SelectionMode to DataGridSelectionMode.Multiple to enable multiple selection on Datagrid.

Clicking rows will now select multiple records at a time. You can now access them by using the SelectedRows parameter and also bind to the SelectedRowsChanged event callback.

Optionally you can use the new Datagrid column DataGridMultiSelectColumn to enable a checkbox column that works exclusively with multiple selection.

You can either use your own MultiSelectTemplate render fragment to customize the input that will appear in the column and trigger the multiple selection by then binding to the provided SelectedChanged event callback or just use the provided default by not specifying a MultiSelectTemplate render fragment. When using this extra column, the top row column, will provide the ability to select or unselect all rows.

Shift-clicking will also select multiple rows starting from the last selected row.

|      |   # | First Name   | Last Name   | Email                       | Salary      |
|------|-----|--------------|-------------|-----------------------------|-------------|
|      |   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|      |   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|      |   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|      |   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|      |   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|      |   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|      |   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|      |   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|      |   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|      |  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          SelectionMode="DataGridSelectionMode.Multiple"
          @bind-SelectedRows="selectedEmployees"
          Responsive>
    <DataGridMultiSelectColumn Width="30px"></DataGridMultiSelectColumn>
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
    <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
        <EditTemplate>
            <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
        </EditTemplate>
    </DataGridColumn>
</DataGrid>
```

```
@code{
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private List<Employee> selectedEmployees;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### RowSelectable &amp; Multiple Selection

Here's an example of combining both RowSelectable and Multiple Selection. We've disabled regular selection through row click, and only enabled selection through clicking the provided multi select checkboxes.

|      |   # | First Name   | Last Name   | Email                       | Salary      |
|------|-----|--------------|-------------|-----------------------------|-------------|
|      |   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|      |   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|      |   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|      |   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|      |   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|      |   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|      |   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|      |   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|      |   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|      |  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          SelectionMode="DataGridSelectionMode.Multiple"
          @bind-SelectedRows="selectedEmployees"
          Responsive
          RowSelectable="RowSelectableHandler">
    <DataGridMultiSelectColumn TItem="Employee" Width="30px"></DataGridMultiSelectColumn>
    <DataGridCommandColumn TItem="Employee" />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
    <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
        <EditTemplate>
            <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
        </EditTemplate>
    </DataGridColumn>
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private List<Employee> selectedEmployees;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private bool RowSelectableHandler( RowSelectableEventArgs<Employee> rowSelectableEventArgs )
        => rowSelectableEventArgs.SelectReason is not DataGridSelectReason.RowClick;
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 