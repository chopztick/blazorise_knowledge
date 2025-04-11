# Blazorise DataGrid: Detail Row Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### DetailRowTemplate

DetailRowTemplate allows you to display nested structure below each row in the grid. One of the examples is “master-detail” relationship between two data-source inside the DataGrid.

For this template the context value is the item from the parent grid.

Once it’s defined a detail-row will be visible for every row in the grid by default. You may change this behaviour by setting DetailRowStartsVisible to false.

If you want to control the visibility of detail-row you can use DetailRowTrigger attribute that can be defined in it’s parent grid.
            Once defined, whenever a user clicks a row, the DetailRowTrigger will be evaluated. You may also use the DataGrid API, ToggleDetailRow to programatically trigger the detail-row.

|    | First Name   |
|----|--------------|
|    | Samuel       |
|    | Irvin        |
|    | Gerald       |
|    | Cora         |
|    | Alfonso      |
|    | Jessie       |
|    | Gregory      |
|    | Maryann      |
|    | Merle        |
|    | Angelina     |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          RowClicked="RowClicked"
          DetailRowTrigger="@(e => DisplayDetailRow(e.Item) && e.Item.Id == selectedEmployee?.Id)"
          Responsive>
    <DataGridColumns>
        <DataGridCommandColumn />
        <DataGridColumn TItem=Employee >
            <DisplayTemplate>
                @if ( DisplayDetailRow( context ) )
                {
                    <Button>
                        <Icon Name="@(rowsWithDetail.Contains( context.Id ) ? IconName.ExpandLess : IconName.ExpandMore)"/>
                    </Button>
                }
            </DisplayTemplate>
        </DataGridColumn>
        <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" />
    </DataGridColumns>
    <DetailRowTemplate>
        @{
            var salaries = context.Salaries;

            <DataGrid TItem="Salary"
                      Data="salaries"
                      Sortable="false"
                      ShowCaptions="false">
                <DataGridCommandColumn />
                <DataGridDateColumn Field="@nameof(Salary.Date)" Caption="Date" />
                <DataGridNumericColumn Field="@nameof(Salary.Total)" Caption="Total" />
            </DataGrid>
        }
    </DetailRowTemplate>
</DataGrid>
```

```
@code{
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private HashSet<int> rowsWithDetail = [];

    void RowClicked(DataGridRowMouseEventArgs<Employee> clickedRow)
    {
        var id = clickedRow.Item.Id;
        if ( !rowsWithDetail.Add( id ) )
            rowsWithDetail.Remove( id );
    }

    bool DisplayDetailRow(Employee employee) => employee.Salaries?.Count > 0;

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