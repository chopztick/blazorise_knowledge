# Blazorise DataGrid: Button Row Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### ButtonRow Template

Provide a ButtonRowTemplate and have the DataGridCommandMode set to either Default or ButtonRow.

The template has access to the internal commands so you’re also able to construct your own buttons on the pager that can also trigger the Datagrid’s CRUD and clear filter operations as shown in the example below:

If you'd like to setup New and/or Edit buttons inside the Button Row or if  is set to , you should take note that if you'd like to customize the Save/Cancel buttons, you should do so by using the  as the Save/Cancel buttons are configured/rendered in this column.

is located inside the Datagrid's , as such the  Parameter should be set to true.

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
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Editable
          Responsive
          ShowPager
          CommandMode="DataGridCommandMode.ButtonRow">
    <DataGridColumns>
        <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
        <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
        <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
        <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
        <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
            <EditTemplate>
                <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
            </EditTemplate>
        </DataGridColumn>
    </DataGridColumns>
    <ButtonRowTemplate>
        <Button Color="Color.Success" Clicked="context.NewCommand.Clicked">New</Button>
        <Button Color="Color.Primary" Disabled="(selectedEmployee is null)" Clicked="context.EditCommand.Clicked">Edit</Button>
        <Button Color="Color.Danger" Disabled="(selectedEmployee is null)" Clicked="context.DeleteCommand.Clicked">Delete</Button>
    </ButtonRowTemplate>
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