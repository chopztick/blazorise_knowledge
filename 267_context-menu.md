# Blazorise DataGrid: Show Context Menu

Show context menu by right clicking on a DataGrid.

## Overview

You may need to know which element the user clicked in some cases so that you can use it in command handling. You might also want to change the menu's contents depending on which element the user clicked (e.g., disable or entirely remove some items from the menu based on a condition).

## Example

### Row Context Menu

To integrate the context menu with the DataGrid, you need to:

1. Use the grid's RowContextMenu event to get the current row model and show the menu.
2. Use the context menu's MouseEventArgs parameter to handle the desired operation.

In this example, the context menu is used to show the menu items, put an item in edit mode and delete items.

|   # | First Name   | Last Name   | Email                       |
|-----|--------------|-------------|-----------------------------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          |
|   4 | Cora         | Conn        | Cora27@yahoo.com            |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        |

```
@using System.Drawing

<DataGrid @ref="@dataGridRef"
          TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          RowContextMenu="@OnRowContextMenu"
          RowContextMenuPreventDefault="true"
          Responsive
          Editable>
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
</DataGrid>

@if ( showContextMenu )
{
    <Div Position="Position.Fixed" Background="Background.Danger" Style="@($"left:{contextMenuPos.X}px;top:{contextMenuPos.Y}px;")">
        <ListGroup>
            <ListGroupItem Clicked="@(()=>OnContextItemEditClicked(contextMenuEmployee))">
                <Icon Name="IconName.Edit" TextColor="TextColor.Secondary" /> Edit
            </ListGroupItem>
            <ListGroupItem Clicked="@(()=>OnContextItemDeleteClicked(contextMenuEmployee))">
                <Icon Name="IconName.Delete" TextColor="TextColor.Danger" /> Delete
            </ListGroupItem>
        </ListGroup>
    </Div>
}
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private DataGrid<Employee> dataGridRef;

    bool showContextMenu = false;
    Employee contextMenuEmployee;
    Point contextMenuPos;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    protected Task OnRowContextMenu( DataGridRowMouseEventArgs<Employee> eventArgs )
    {
        showContextMenu = true;
        contextMenuEmployee = eventArgs.Item;
        contextMenuPos = eventArgs.MouseEventArgs.Client;

        return Task.CompletedTask;
    }

    protected async Task OnContextItemEditClicked( Employee employee )
    {
        await dataGridRef.Edit( employee );

        showContextMenu = false;
    }

    protected async Task OnContextItemDeleteClicked( Employee employee )
    {
        await dataGridRef.Delete( employee );

        showContextMenu = false;
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 