# Blazorise DataGrid: Filtering

Filtering allows you to view particular records based on filter criteria.

## Overview

Filtering in the Blazorise DataGrid can be done using the built-in filtering functionality or by using a custom filter component. The built-in filter allows you to quickly filter data by a specific column using a text box. You can also specify the filter mode, such as "contains" or "starts with".

## Examples

### Filtering

Use an attribute Filterable to enable or disable automatic filtering in grid component.

Default method for filtering is Contains. If you want to change it you can set the FilterMethod attribute on data grid. Supported methods are:

Contains search for any occurrence (default)
StartsWith search only the beginning
EndsWith search only the ending
Equals search must match the entire value
NotEquals opposite of Equals

| Name    |
|---------|
|         |
| David   |
| Mladen  |
| John    |
| Ana     |
| Jessica |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Filterable
          FilterMethod="DataGridFilterMethod.StartsWith"
          Responsive>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
</DataGrid>
```

```
@code{
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "Mladen" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };
}
```

### Column Filtering

Similar to the DataGrid filtering, it is also possible to use filtering on a per-column basis by specifying FilterMethod on DataGridColumn.

The following example sets the column filtering to FilterMethod.StartsWith.

| Name    |
|---------|
|         |
| David   |
| MLaden  |
| John    |
| Ana     |
| Jessica |

```
<DataGrid @ref="dataGrid"
          TItem="Employee"
          Data="@employeeList"
          Responsive
          Filterable>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false" FilterMethod="DataGridColumnFilterMethod.StartsWith"></DataGridColumn>
</DataGrid>
```

```
@code {
    private DataGrid<Employee> dataGrid;
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "MLaden" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };
}
```

### Menu Mode Filtering

Similar to the previous Column Filtering example, we can enable the DataGridFilterMode.Menu to visually show the column filtering.

| First Name Contains Starts With Ends WithEquals Not Equals    Filter Clear Filter   | Last Name Contains Starts With Ends WithEquals Not Equals    Filter Clear Filter   | Gender Contains Starts With Ends WithEquals Not Equals  MaleFemaleDiverse  Filter Clear Filter   |   Children Equals Not EqualsGreater Than Greater Than or Equal Less Than Less Than or Equal Between      Filter Clear Filter |
|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| David                                                                               | Moreira                                                                            | M                                                                                                |                                                                                                                            0 |
| MLaden                                                                              | Macanovic                                                                          | M                                                                                                |                                                                                                                            1 |
| John                                                                                | Doe                                                                                | M                                                                                                |                                                                                                                            2 |
| Ana                                                                                 | Chamberlain                                                                        | F                                                                                                |                                                                                                                            5 |
| Jessica                                                                             | Winston                                                                            | F                                                                                                |                                                                                                                            2 |

```
<DataGrid @ref="dataGrid"
          TItem="Employee"
          Data="@employeeList"
          Responsive
          Filterable
          FilterMode="DataGridFilterMode.Menu">
     <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="First Name" Editable="false" FilterMethod="DataGridColumnFilterMethod.StartsWith"></DataGridColumn>
    <DataGridColumn Field="@nameof( Employee.LastName )" Caption="Last Name" Editable="false"></DataGridColumn>
    <DataGridSelectColumn TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Editable Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
    <DataGridNumericColumn Field="@nameof(Employee.Childrens)" Caption="Children" Editable />
</DataGrid>
```

```
@code{
    private DataGrid<Employee> dataGrid;
    private List<Employee> employeeList = new() { new() { FirstName = "David", LastName = "Moreira", Gender = "M", Childrens = 0 }, new() { FirstName = "MLaden", LastName = "Macanovic", Gender = "M", Childrens = 1 }, new() { FirstName = "John", LastName = "Doe", Gender = "M", Childrens = 2 }, new() { FirstName = "Ana", LastName = "Chamberlain", Gender = "F", Childrens = 5 }, new() { FirstName = "Jessica", LastName = "Winston", Gender = "F", Childrens = 2 } };
}
```

### Menu Mode Filtering : Template

When using Menu Mode Filtering you may also use the FilterTemplate to customize the filter input to your liking.

| First Name Contains Starts With Ends WithEquals Not Equals     Filter  Clear   | Last Name Contains Starts With Ends WithEquals Not Equals     Filter  Clear   | Gender Contains Starts With Ends WithEquals Not Equals     Filter  Clear   |   Children Equals Not EqualsGreater Than Greater Than Or Equal Less Than Less Than Or Equal Between     Filter  Clear |
|--------------------------------------------------------------------------------|-------------------------------------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| Liam                                                                           | Smith                                                                         | M                                                                          |                                                                                                                     0 |
| Noah                                                                           | Johnson                                                                       | M                                                                          |                                                                                                                     1 |
| Ethan                                                                          | Brown                                                                         | M                                                                          |                                                                                                                     2 |
| Olivia                                                                         | Davis                                                                         | F                                                                          |                                                                                                                     5 |
| Emma                                                                           | Wilson                                                                        | F                                                                          |                                                                                                                     2 |

```
<DataGrid @ref="dataGrid"
          TItem="Employee"
          Data="@employeeList"
          Responsive
          Filterable
          FilterMode="DataGridFilterMode.Menu">
    <DataGridColumns>
        <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="First Name" Editable="false" FilterMethod="DataGridColumnFilterMethod.StartsWith"></DataGridColumn>
        <DataGridColumn Field="@nameof( Employee.LastName )" Caption="Last Name" Editable="false"></DataGridColumn>
        <DataGridSelectColumn TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Editable Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
        <DataGridNumericColumn Field="@nameof(Employee.Childrens)" Caption="Children" Editable />
    </DataGridColumns>
    <FilterMenuTemplate>
        <Row>
            <Column ColumnSize="ColumnSize.Is4">
                <Select TValue="DataGridColumnFilterMethod" SelectedValue="@context.GetFilterMethod()" SelectedValueChanged="e => { context.FilterMethodChanged.InvokeAsync(e); }">
                    @{
                        var isNumericOrDate = context.Column.ColumnType == DataGridColumnType.Numeric || context.Column.ColumnType == DataGridColumnType.Date;
                    }

                    @if ( !isNumericOrDate )
                    {
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.Contains">Contains</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.StartsWith">Starts With</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.EndsWith">Ends With</SelectItem>
                    }
                    <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.Equals">Equals</SelectItem>
                    <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.NotEquals">Not Equals</SelectItem>
                    @if ( isNumericOrDate )
                    {
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.GreaterThan">Greater Than</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.GreaterThanOrEqual">Greater Than Or Equal</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.LessThan">Less Than</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.LessThanOrEqual">Less Than Or Equal</SelectItem>
                        <SelectItem TValue="DataGridColumnFilterMethod" Value="@DataGridColumnFilterMethod.Between">Between</SelectItem>
                    }
                </Select>
            </Column>

            <Column ColumnSize="ColumnSize.Is4">
                <Field @key=context.GetFilterMethod()>
                    @if ( context.GetFilterMethod() == DataGridColumnFilterMethod.Between )
                    {
                        <TextEdit Text="@GetFilterValue1(context)" TextChanged="@((newValue) => SetFilterValue1(context.Column.Filter, newValue))" />
                        <TextEdit Text="@GetFilterValue2(context)" TextChanged="@((newValue) => SetFilterValue2(context.Column.Filter, newValue))" />
                    }
                    else
                    {
                        <TextEdit Text="@context.GetSearchValue()?.ToString()" TextChanged="@((newValue) => context.Column.Filter.SearchValue = newValue)" />
                    }
                </Field>
            </Column>

            <Column ColumnSize="ColumnSize.Is4">
                <Button Clicked="context.Filter" Color="Color.Primary"><Icon Name="IconName.Filter"></Icon> Filter</Button>
                <Button Clicked="context.ClearFilter" Color="Color.Light"><Icon Name="IconName.Clear"></Icon> Clear</Button>
            </Column>
        </Row>
    </FilterMenuTemplate>
</DataGrid>
```

```
@code {
    private DataGrid<Employee> dataGrid;
    private List<Employee> employeeList = new()
    {
        new() { FirstName = "Liam", LastName = "Smith", Gender = "M", Childrens = 0 },
        new() { FirstName = "Noah", LastName = "Johnson", Gender = "M", Childrens = 1 },
        new() { FirstName = "Ethan", LastName = "Brown", Gender = "M", Childrens = 2 },
        new() { FirstName = "Olivia", LastName = "Davis", Gender = "F", Childrens = 5 },
        new() { FirstName = "Emma", LastName = "Wilson", Gender = "F", Childrens = 2 },
    };

    private string GetFilterValue1( FilterColumnContext<Employee> context )
    {
        return ( context.GetSearchValue() as object[] )?[0]?.ToString();
    }

    private string GetFilterValue2( FilterColumnContext<Employee> context )
    {
        return ( context.GetSearchValue() as object[] )?[1]?.ToString();
    }

    private void SetFilterValue1( FilterContext<Employee> context, object value1 )
    {
        if ( context.SearchValue is not object[] )
        {
            context.SearchValue = new object[2];
        }

        ( context.SearchValue as object[] )[0] = value1;
    }

    private void SetFilterValue2( FilterContext<Employee> context, object value2 )
    {
        if ( context.SearchValue is not object[] )
        {
            context.SearchValue = new object[2];
        }

        ( context.SearchValue as object[] )[1] = value2;
    }
}
```

### Custom Filtering

Regular filter works on per field basis. To enable advanced search capabilities you can use an attribute CustomFilter.

Filter API is fairly straightforward. All you need is to attach CustomFilter to a function and bind search value to TextEdit field. DataGrid will automatically respond to entered value.

| Name    |
|---------|
| David   |
| MLaden  |
| John    |
| Ana     |
| Jessica |

Custom Filter:

```
Custom Filter: <TextEdit Text="@customFilterValue" TextChanged="@OnCustomFilterValueChanged"></TextEdit>

<DataGrid @ref="dataGrid"
          TItem="Employee"
          Data="@employeeList"
          CustomFilter="@OnCustomFilter"
          Responsive>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
</DataGrid>
```

```
@code{
    private DataGrid<Employee> dataGrid;
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "MLaden" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };

    private string customFilterValue;

    private Task OnCustomFilterValueChanged( string e )
    {
        customFilterValue = e;
        return dataGrid.Reload();
    }

    private bool OnCustomFilter( Employee model )
    {
        // We want to accept empty value as valid or otherwise
        // datagrid will not show anything.
        if ( string.IsNullOrEmpty( customFilterValue ) )
            return true;

        return model.FirstName?.Contains( customFilterValue, StringComparison.OrdinalIgnoreCase ) == true;
    }

}
```

### Custom Column Filtering

Similar to the DataGrid custom filtering, it is also possible to use custom filtering on a per-column basis.

You can define your editor with custom filtering to filter column values. You can see the dropdown menu to filter by gender in the following example by specifying &lt;FilterTemplate&gt; on DataGridColumn.

| Name    | Gender            |
|---------|-------------------|
|         | MaleFemaleDiverse |
| David   | M                 |
| Mladen  | M                 |
| John    | M                 |
| Ana     | F                 |
| Jessica | F                 |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Filterable
          Responsive>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
    <DataGridSelectColumn CustomFilter="@OnGenderCustomFilter" TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Editable Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
</DataGrid>
```

```
@code{
    private List<Employee> employeeList = new() { new() { FirstName = "David", Gender = "M" }, new() { FirstName = "Mladen", Gender = "M" }, new() { FirstName = "John", Gender = "M" }, new() { FirstName = "Ana", Gender = "F" }, new() { FirstName = "Jessica", Gender = "F" } };

    private bool OnGenderCustomFilter( object itemValue, object searchValue )
    {
        if ( searchValue is string genderFilter )
        {
            return genderFilter == "*" || genderFilter == itemValue?.ToString();
        }

        return true;
    }

}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 