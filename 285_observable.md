# Blazorise DataGrid: Observable Data

The DataGrid Observable Data feature allows you to bind in memory observable data collections.

### Observable Data

By default, DataGrid does not listen to changes in the underlying data collection.
            This means that if you change the collection, by calling methods like, Add or Remove, the DataGrid will not be updated.

This is in the interest of performance and as such we recommended the following, either:
            Invoke gridRef.Reload(); when you're done mutating your collection
Have your data be observable by using any implementation of the INotifyCollectionChanged, like the ObservableCollection. The example below ilustrates this.

| Name   |
|--------|
| Name 1 |
| Name 2 |

```
@using System.Collections.ObjectModel;

<Button Clicked="OnAddItemClick" Color="Color.Primary">Add Item</Button>
<Button Clicked="OnRemoveItemClick" Color="Color.Danger">Remove Item</Button>

<DataGrid TItem="Employee"
          Data="@items"
          Responsive>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable="false"></DataGridColumn>
</DataGrid>
```

```
@code {
    private ObservableCollection<Employee> items = new() {
        new() { FirstName = "Name 1" },
        new() { FirstName = "Name 2" }
    };

    private Task OnAddItemClick()
    {
        items.Add( new Employee { FirstName = $"Name {items.Count + 1}" } );

        return Task.CompletedTask;
    }

    private Task OnRemoveItemClick()
    {
        if ( items.Count > 0 )
            items.RemoveAt( 0 );

        return Task.CompletedTask;
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 