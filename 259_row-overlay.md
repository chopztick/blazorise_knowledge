# Blazorise DataGrid: Row Overlay

When enabled, the Row Overlay feature allows you to display supplementary data or contextual information directly on top of specific rows within the DataGrid.

### Row Overlay

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
    <DataGridColumns>
        <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
    </DataGridColumns>
    <RowOverlayTemplate>
        <Div>
            <Button Color="Color.Primary" Size="Size.ExtraSmall"> <Icon Name="IconName.User" /> User Details > </Button>
            <Button Color="Color.Secondary" Size="Size.ExtraSmall"> <Icon Name="IconName.Building" /> Company Details > </Button>
        </Div>
    </RowOverlayTemplate>
</DataGrid>
```

```
@code {
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "MLaden" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 