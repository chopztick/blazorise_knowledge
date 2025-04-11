# Blazorise DataGrid: Columns

DataGrid provides many types of columns. You can use built-in columns such as text, numeric, date, checkbox, select, etc to automatically create specialized content.

### Default Column

Default column template for text values. In this example, we are using the default column template for the  property.

| Email                      | New          |
|----------------------------|--------------|
|                            | Clear Filter |
| Samuel.Collier62@gmail.com | EditDelete   |
| Irvin.Ziemann@gmail.com    | EditDelete   |
| Gerald82@yahoo.com         | EditDelete   |
| Cora27@yahoo.com           | EditDelete   |
| Alfonso.DAmore@hotmail.com | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Check Column

Column template for boolean values

| Active   | New          |
|----------|--------------|
|          | Clear Filter |
|          | EditDelete   |
|          | EditDelete   |
|          | EditDelete   |
|          | EditDelete   |
|          | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridCheckColumn Field="@nameof(Employee.IsActive)" Caption="Active" Editable />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Date Column

Column template for datetime values

| Date Of Birth         | New          |
|-----------------------|--------------|
|                       | Clear Filter |
| 8/26/1970 12:04:15 PM | EditDelete   |
| 5/25/1974 3:58:51 AM  | EditDelete   |
| 4/29/1969 7:52:08 PM  | EditDelete   |
| 2/12/1984 9:18:03 PM  | EditDelete   |
| 11/6/1983 2:08:14 PM  | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridDateColumn Field="@nameof(Employee.DateOfBirth)" Caption="Date Of Birth" Editable />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Date Column with Native Mode

Column template for datetime values. Set NativeInputMode if you prefer to use the native html input variant of the date input.

| Date Of Birth         | New          |
|-----------------------|--------------|
|                       | Clear Filter |
| 8/26/1970 12:04:15 PM | EditDelete   |
| 5/25/1974 3:58:51 AM  | EditDelete   |
| 4/29/1969 7:52:08 PM  | EditDelete   |
| 2/12/1984 9:18:03 PM  | EditDelete   |
| 11/6/1983 2:08:14 PM  | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridDateColumn Field="@nameof(Employee.DateOfBirth)" Caption="Date Of Birth" Editable NativeInputMode />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Numeric Column

Column template for numeric values

| Salary   | New          |
|----------|--------------|
|          | Clear Filter |
| 86030.41 | EditDelete   |
| 61781.31 | EditDelete   |
| 58810.75 | EditDelete   |
| 84414.66 | EditDelete   |
| 69318.29 | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridNumericColumn Field="@nameof(Employee.Salary)" Caption="Salary" Editable />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Numeric Column with Native Mode

Column template for numeric values. Set NativeInputMode if you prefer to use the native html input variant of the numeric input.

| Salary   | New          |
|----------|--------------|
|          | Clear Filter |
| 86030.41 | EditDelete   |
| 61781.31 | EditDelete   |
| 58810.75 | EditDelete   |
| 84414.66 | EditDelete   |
| 69318.29 | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridNumericColumn Field="@nameof(Employee.Salary)" Caption="Salary" Editable NativeInputMode />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Select Column

Column template for selectable values

| Gender            | New          |
|-------------------|--------------|
| MaleFemaleDiverse | Clear Filter |
| M                 | EditDelete   |
| M                 | EditDelete   |
| M                 | EditDelete   |
| D                 | EditDelete   |
| F                 | EditDelete   |

```
<DataGrid TItem="Employee" Data="@employeeList" PageSize="5" Responsive Editable Filterable>
    <DataGridSelectColumn TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Editable
                          Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

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