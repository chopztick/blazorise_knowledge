# Blazorise DataGrid: Fixed Columns

This feature allows users to anchor cells or columns to either the left (Start) or right (End) side of the DataGrid. This ensures that the fixed cells or columns remain visible and in place as users scroll through the table. To utilize this feature, set the FixedPosition attribute to TableColumnFixedPosition.Start for left-side anchoring or TableColumnFixedPosition.End for right-side anchoring on a cell. Additionally, you must enable fixed columns on a table with the FixedColumns attribute.

The functionality is particularly useful for financial tables, reports, and dashboards, where key information needs to remain visible while scrolling through large amounts of data.

### Fixed Columns

|   # | First Name   | Last Name   | Email                       | City              | Zip        | Date Of Birth   |   Childrens | Gender   | Salary      | Active   |
|-----|--------------|-------------|-----------------------------|-------------------|------------|-----------------|-------------|----------|-------------|----------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | New Lura          | 91848-4714 | 26.08.1970      |           3 | M        | 86 030,41 € |          |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | Modestomouth      | 16505-8405 | 25.05.1974      |           3 | M        | 61 781,31 € |          |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | Theresashire      | 28612      | 29.04.1969      |           1 | M        | 58 810,75 € |          |
|   4 | Cora         | Conn        | Cora27@yahoo.com            | North Art         | 10437-2253 | 12.02.1984      |           5 | D        | 84 414,66 € |          |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | East Carolefort   | 87912-3933 | 06.11.1983      |           5 | F        | 69 318,29 € |          |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | Mayrafurt         | 34306      | 02.10.1995      |           4 | M        | 78 566,12 € |          |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       | West Marcelleside | 57895      | 15.03.1978      |           1 | F        | 57 456,82 € |          |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | Boehmview         | 38859-0368 | 01.07.1970      |           5 | D        | 89 153,38 € |          |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            | North Erlingport  | 48154-3034 | 24.06.1993      |           5 | F        | 55 349,94 € |          |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        | Melyssaview       | 72291-1146 | 18.09.1992      |           3 | D        | 73 625,86 € |          |

- First
- Prev
- 1
- 2
- 3
- 4
- 5
- 12345
- Next
- Last
- 5102550100250
- items per page

1 - 10 of 499 items

499 items

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          FixedColumns
          ShowPager
          ShowPageSizes
          @bind-SelectedRow="@selectedEmployee">
    <DataGridColumns>
        <DataGridColumn TextAlignment="TextAlignment.Center" TItem="Employee" Field="@nameof( Employee.Id )" Caption="#" Width="60px" FixedPosition="TableColumnFixedPosition.Start" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.FirstName )" Caption="First Name" Width="150px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.LastName )" Caption="Last Name" Width="150px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Email )" Caption="Email" Width="250px" FixedPosition="TableColumnFixedPosition.Start" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.City )" Caption="City" Width="150px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Zip )" Caption="Zip" Width="100px" />
        <DataGridDateColumn TItem="Employee" Field="@nameof( Employee.DateOfBirth )" DisplayFormat="{0:dd.MM.yyyy}" Caption="Date Of Birth" Width="100px" />
        <DataGridNumericColumn TItem="Employee" Field="@nameof( Employee.Childrens )" Caption="Childrens" Filterable="false" Width="100px" />
        <DataGridSelectColumn TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" Width="100px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Salary )" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" TextAlignment="TextAlignment.End" Width="100px" FixedPosition="TableColumnFixedPosition.End" />
        <DataGridCheckColumn TItem="Employee" Field="@nameof(Employee.IsActive)" Caption="Active" Filterable="false" Width="100px" />
    </DataGridColumns>
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 