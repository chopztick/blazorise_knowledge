# Blazorise DataGrid: Sorting

Sorting allows you to arrange data in ascending or descending order. To sort a column, click its header.

## Overview

All columns can be sorted automatically if the option Sortable is enabled on the column.

Use SortField if you would like to set a different field or property to be considered by the sorting mechanism on a certain column.

## Examples

### Single

By default the DataGrid sorting mode is single column based.

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
          Sortable
          SortMode="DataGridSortMode.Single">
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

### Multiple

You may also change the DataGrid sorting mode to multiple, to allow sorting on multiple columns.

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
          Sortable
          SortMode="DataGridSortMode.Multiple">
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

### SortField

The SortField feature, allows you to define a different Property or Field of the Item to be considered by the sorting mechanism.

In this example, we define the Sort Field of the Childrens Column to be the calculated property ChildrensPerSalary.

|   # | First Name   | Last Name   | Email                        | Salary      |   Childrens |
|-----|--------------|-------------|------------------------------|-------------|-------------|
|  81 | Pat          | Rohan       | Pat_Rohan@gmail.com          | 50 151,72 € |           5 |
| 485 | Gina         | Bruen       | Gina60@gmail.com             | 50 564,33 € |           5 |
| 103 | Helen        | Mueller     | Helen_Mueller@gmail.com      | 51 704,43 € |           5 |
| 149 | Alberto      | Bernhard    | Alberto.Bernhard41@gmail.com | 52 655,29 € |           5 |
| 252 | Mark         | Bins        | Mark.Bins@hotmail.com        | 52 790,83 € |           5 |
|  40 | Bobbie       | Rogahn      | Bobbie.Rogahn7@yahoo.com     | 52 889,16 € |           5 |
| 215 | Don          | Altenwerth  | Don.Altenwerth32@gmail.com   | 52 897,75 € |           5 |
| 354 | Paula        | Kautzer     | Paula73@hotmail.com          | 53 365,86 € |           5 |
| 498 | Susie        | Casper      | Susie.Casper52@yahoo.com     | 53 448,48 € |           5 |
| 314 | Kristen      | Huel        | Kristen.Huel@gmail.com       | 54 689,50 € |           5 |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Responsive
          Sortable
          SortMode="DataGridSortMode.Single">
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
    <DataGridNumericColumn TItem="Employee" Field="@nameof( Employee.Childrens )" Caption="Childrens" Editable Filterable="false"
                           SortField="@nameof( Employee.ChildrensPerSalary )" SortDirection="SortDirection.Descending" />
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

### SortComparer

The SortComparer feature allows you to define a custom sorting logic for a column by specifying an IComparer&lt;TItem&gt; implementation.
            This is useful when you want to sort data based on complex or calculated criteria that go beyond the default alphabetical or numerical order.
            Note that this comparer can only be used with in-memory data.

In this example, a custom comparer is applied to sort by the FirstName length, and then, for items with the same first name length, alphabetically by LastName.
            Sort by Full Name column to see it in action.
            This demonstrates how to implement a multi-criteria sorting mechanism in Blazorise's DataGrid.

|   # | Full Name        | Email                       | Salary      |
|-----|------------------|-----------------------------|-------------|
|   1 | Samuel Collier   | Samuel.Collier62@gmail.com  | 86 030,41 € |
|   2 | Irvin Ziemann    | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|   3 | Gerald Pollich   | Gerald82@yahoo.com          | 58 810,75 € |
|   4 | Cora Conn        | Cora27@yahoo.com            | 84 414,66 € |
|   5 | Alfonso D'Amore  | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|   6 | Jessie Wilkinson | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|   7 | Gregory Renner   | Gregory63@hotmail.com       | 57 456,82 € |
|   8 | Maryann Hilpert  | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|   9 | Merle Pacocha    | Merle3@gmail.com            | 55 349,94 € |
|  10 | Angelina Ward    | Angelina42@gmail.com        | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Responsive
          Sortable
          SortMode="DataGridSortMode.Single">
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridNumericColumn TItem="Employee" Field="@nameof(Employee.FirstName)" Caption="Full Name" Filterable="false" SortComparer="new EmployeeNameComparer()">
        <DisplayTemplate>
            @($"{context.FirstName} {context.LastName}")
        </DisplayTemplate>
    </DataGridNumericColumn>
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

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    public class EmployeeNameComparer : Comparer<Employee>
    {
        public override int Compare( Employee x, Employee y )
        {
            // Null checks
            if ( x is null && y is null ) return 0;
            if ( x is null ) return -1;
            if ( y is null ) return 1;

            // Compare by length of FirstName
            int firstNameLengthComparison = x.FirstName.Length.CompareTo(y.FirstName.Length);

            // If FirstName lengths are the same, compare alphabetically by LastName
            return firstNameLengthComparison != 0
                ? firstNameLengthComparison
                : string.CompareOrdinal(x.LastName, y.LastName);
        }
    }
}
```

### ApplySorting

You can use the ApplySorting method to programmatically specify the columns to sort by.

In this example, there are two buttons to change the sort order programmatically.

|   # | First Name   | Last Name   | Email                       |   Salary |   Childrens | Gender   |
|-----|--------------|-------------|-----------------------------|----------|-------------|----------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  |  86030.4 |           3 | M        |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     |  61781.3 |           3 | M        |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          |  58810.8 |           1 | M        |
|   4 | Cora         | Conn        | Cora27@yahoo.com            |  84414.7 |           5 | D        |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  |  69318.3 |           5 | F        |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  |  78566.1 |           4 | M        |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       |  57456.8 |           1 | F        |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com |  89153.4 |           5 | D        |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            |  55349.9 |           5 | F        |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        |  73625.9 |           3 | D        |

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

1 - 10 of 499 items

499 items

```
<Button Color="Color.Secondary" Clicked="OnResetClicked">Reset sorting</Button>
<Button Color="Color.Primary" Clicked="OnPredefinedClicked">Apply predefined sorting</Button>

<DataGrid @ref="dataGrid"
          TItem="Employee"
          Data="@employeeList"
          Responsive
          Sortable
          SortMode="DataGridSortMode.Multiple"
          ShowPager="true">
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" />
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" />
    <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" />
    <DataGridNumericColumn TItem="Employee" Field="@nameof( Employee.Childrens )" Caption="Childrens" />
    <DataGridColumn Field="@nameof(Employee.Gender)" Caption="Gender" />
</DataGrid>
```

```
@code {
    [Inject] public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private DataGrid<Employee> dataGrid;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private Task OnResetClicked() => dataGrid.ApplySorting(Array.Empty<DataGridSortColumnInfo>());

    private Task OnPredefinedClicked() => dataGrid.ApplySorting(
        new DataGridSortColumnInfo(nameof(Employee.Childrens), SortDirection.Descending),
        new DataGridSortColumnInfo(nameof(Employee.Gender), SortDirection.Ascending)
        );
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 