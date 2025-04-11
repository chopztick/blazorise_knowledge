# Blazorise DataGrid: Loading Template

Blazor includes templated components that can accept one or more UI segments as input and render them as part of the component during component rendering. DataGrid is a templated Blazor component that lets you customize various parts of the user interface with template parameters. It enables you to generate custom components or content using your own logic.

### Loading Templates

If you want to change display of content, while grid is empty or ReadData is executing, you can use following templates:

- EmptyTemplate
- LoadingTemplate

| #                        | First Name               | Last Name                | Email                    | Salary                   |
|--------------------------|--------------------------|--------------------------|--------------------------|--------------------------|
| No employees were found! | No employees were found! | No employees were found! | No employees were found! | No employees were found! |

```
<DataGrid @ref="datagridRef"
          TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          TotalItems="@totalEmployees"
          ReadData="@LoadEmployeesFromService"
          Responsive>
    <DataGridColumns>
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
    </DataGridColumns>
    <EmptyTemplate>
        <div class="box">
            No employees were found!
        </div>
    </EmptyTemplate>
    <LoadingTemplate>
        <Progress @ref="progressRef" Color="Color.Primary" Max="100" Value="progress" />
    </LoadingTemplate>
</DataGrid>

<Button Background="Background.Primary" Color="Color.Light" Clicked="() => datagridRef.Reload()">Load</Button>
```

```
@code{
    protected DataGrid.DataGrid<Employee> datagridRef;
    protected Progress progressRef;
    protected int progress;
    protected Employee selectedEmployee;
    protected int totalEmployees = 0;
    protected List<Employee> employeeList;

    public async Task LoadEmployeesFromService( DataGridReadDataEventArgs<Employee> e )
    {
        /*
        * This can be call to anything like calling an api to load employees.
        * During execution 'LoadingTemplate' will be displayed.
        * If your api call returns empty result, then 'EmptyTemplate' will be displayed,
        * this way you have proper feedback, for when your datagrid is loading or empty.
        */
        progress = 0;
        await InvokeAsync( StateHasChanged );

        await Task.Delay( 500 );
        progress = 25;
        await InvokeAsync( StateHasChanged );

        await Task.Delay( 500 );
        progress = 50;
        await InvokeAsync( StateHasChanged );

        await Task.Delay( 500 );
        progress = 75;
        await InvokeAsync( StateHasChanged );


        await Task.Delay( 500 );
        progress = 100;
        await InvokeAsync( StateHasChanged );
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 