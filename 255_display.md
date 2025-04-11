# Blazorise DataGrid: Display Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### DisplayTemplate

Display template is using  as a context value.

| Date Of Birth       |
|---------------------|
| 8/26/1970 | Age: 55 |
| 5/25/1974 | Age: 51 |
| 4/29/1969 | Age: 56 |
| 2/12/1984 | Age: 41 |
| 11/6/1983 | Age: 42 |
| 10/2/1995 | Age: 30 |
| 3/15/1978 | Age: 47 |
| 7/1/1970 | Age: 55  |
| 6/24/1993 | Age: 32 |
| 9/18/1992 | Age: 33 |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Responsive>
    <DataGridNumericColumn Field="@nameof(Employee.DateOfBirth)" Caption="Date Of Birth" Editable>
    <DisplayTemplate>
        @{
            var date = ( context as Employee )?.DateOfBirth;

            if ( date != null )
            {
                @($"{date.Value.ToShortDateString()} | Age: {( DateTime.Now.Year - date.Value.Year )}")
            }
        }
    </DisplayTemplate>
</DataGridNumericColumn>
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