# Blazorise DataGrid: Commands Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### Command Templates

If you want to change the default command buttons, you can use following templates:

- NewCommandTemplate
- EditCommandTemplate
- SaveCommandTemplate
- CancelCommandTemplate
- DeleteCommandTemplate
- ClearFilterCommandTemplate

| New        |   # | First Name   | Last Name   | Email                       | Salary      |
|------------|-----|--------------|-------------|-----------------------------|-------------|
| EditDelete |   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
| EditDelete |   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
| EditDelete |   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
| EditDelete |   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
| EditDelete |   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
| EditDelete |   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
| EditDelete |   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
| EditDelete |   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
| EditDelete |   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
| EditDelete |  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Editable
          Responsive>
    <DataGridCommandColumn>
        <NewCommandTemplate>
            <Button Color="Color.Success" Clicked="@context.Clicked">New</Button>
        </NewCommandTemplate>
        <EditCommandTemplate>
            <Button Color="Color.Primary" Clicked="@context.Clicked">Edit</Button>
        </EditCommandTemplate>
    </DataGridCommandColumn>
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