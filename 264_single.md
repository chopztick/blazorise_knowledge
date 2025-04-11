# Blazorise DataGrid: Single Selection

The DataGrid allows you to select rows with the click of a mouse.

### Selecting

If you need to control how and when the grid row will be selected you can use a  event handler. Here's a simple example where John's row is not selectable:

| Name    |
|---------|
| David   |
| MLaden  |
| John    |
| Ana     |
| Jessica |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          RowSelectable=@((x)=> x.Item.FirstName != "John")
          Responsive>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
</DataGrid>
```

```
@code{
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "MLaden" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 