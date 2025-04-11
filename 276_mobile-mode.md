# Blazorise DataGrid: Mobile Mode

Show the DataGrid table in a vertical mode.

## Overview

With the Mobile Mode enabled, the table will render a dedicated layout for mobile devices where the columns are stacked on top of each other.

## Examples

### Mobile Mode

Click on the mobile icon in the top right corner to see the mobile mode in action.

|   # | First Name   | Last Name   | Email                       | Salary      |
|-----|--------------|-------------|-----------------------------|-------------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Responsive
          ResponsiveMode="@TableResponsiveMode.Mobile">
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