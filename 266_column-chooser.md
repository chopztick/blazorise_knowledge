# Blazorise DataGrid: Column Chooser

Enable Column Chooser to allow users to show or hide columns in the DataGrid.

## Overview

Enable the feature by setting ColumnChooser to true.

## Example

- First
- Prev
- 1
- 2
- 3
- 123
- Next
- Last
- 5102550100250
- items per page

1 - 10 of 25 items

25 items

```
<DataGrid TItem="Employee"
          Data="inMemoryData"
          Responsive
          ShowColumnChooser
          PagerPosition="DataGridPagerPosition.Top"
          ShowPager
          ShowPageSizes
          ColumnDisplayingChanged="@ColumnDisplayChanged">
</DataGrid>
```

```
@code {

    [Inject] EmployeeData EmployeeData { get; set; }

    private IEnumerable<Employee> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 );
        await base.OnInitializedAsync();
    }

    protected void ColumnDisplayChanged( ColumnDisplayChangedEventArgs<Employee> args )
    {
        Console.WriteLine( $"Column: {args.Column.Field} | Display: {args.Display}" );
    }
}
```

## Positioning example

```
<DataGrid TItem="Employee"
          Data="inMemoryData"
          Responsive
          ShowColumnChooser
          PagerPosition="DataGridPagerPosition.Top"
          PagerOptions="new DataGridPagerOptions() { ColumnChooserPosition = PagerElementPosition.End }">
</DataGrid>
```

```
@code {

    [Inject] EmployeeData EmployeeData { get; set; }

    private IEnumerable<Employee> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 );
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