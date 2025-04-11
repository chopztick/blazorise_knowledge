# Blazorise DataGrid: Edit Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### EditTemplate

Edit template will give you a way to handle the editing of grid cell values. For this template  is used as a  value. Use it to get or set the cell values.

| New        | Salary      |
|------------|-------------|
| EditDelete | 86 030,41 € |
| EditDelete | 61 781,31 € |
| EditDelete | 58 810,75 € |
| EditDelete | 84 414,66 € |
| EditDelete | 69 318,29 € |
| EditDelete | 78 566,12 € |
| EditDelete | 57 456,82 € |
| EditDelete | 89 153,38 € |
| EditDelete | 55 349,94 € |
| EditDelete | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Editable
          Responsive>
    <DataGridCommandColumn />
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