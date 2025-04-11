# Blazorise DataGrid: Resizing

Adjust the width of columns in the DataGrid to better fit the data.

## Overview

With the resizable column feature, users can easily adjust the width of columns in the DataGrid to better fit the data they are viewing. This can be particularly useful when working with large sets of data, where some columns may have longer or shorter data than others. By allowing users to resize columns, they can more easily read and understand the data in the grid.

## Examples

### Resizable

The resizable column feature is easy to enable in the Blazorise DataGrid. Just define the  and  parameters.

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
<Field>
    <FieldLabel>
        Resize Mode
    </FieldLabel>
    <FieldBody>
        <Select @bind-SelectedValue="@resizeMode">
            <SelectItem Value="TableResizeMode.Header">Header</SelectItem>
            <SelectItem Value="TableResizeMode.Columns">Columns</SelectItem>
        </Select>
    </FieldBody>
</Field>

<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Responsive
          Resizable
          ResizeMode="@resizeMode">
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
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private TableResizeMode resizeMode = TableResizeMode.Header;

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