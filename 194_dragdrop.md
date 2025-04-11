# Blazorise Drag &amp; Drop component

Quickly drag and drop elements between the containers.

The Drag &amp; Drop is comprised of DropContainer and DropZone components. The DropContainer is used as a container for all items that are being dragged,
    along with the DropZone's that are basically an areas to drag the items.

- &lt; DropContainer&gt; the main container.
- &lt;DropContainer&gt; the main container.
    - &lt;DropZone&gt; wrapper for drop zone content.

## Examples

### Basic

To start, first define a DropContainer and assign the Items to it.

Next you define DropZone's and assign them a unique Name. The Name, along with the ItemsFilter parameter is used to determine to which DropZone an item will belong.

The callback ItemDropped is used to update the data item, when a drag operation has finished.

#### Basket

<!-- image -->

Apple

<!-- image -->

Bananas

<!-- image -->

Broccoli

<!-- image -->

Cherry

#### Fruit

<!-- image -->

Lemon

<!-- image -->

Strawberry

#### Vegetable

<!-- image -->

Cabbage

```
<DropContainer TItem="DropItem" Items="@items" ItemsFilter="@((item, dropZone) => item.Group == dropZone)" ItemDropped="@ItemDropped" Flex="Flex.Wrap.Grow.Is1">
    <ChildContent>
        <DropZone TItem="DropItem" Name="Basket" Border="Border.Rounded" Background="Background.Light" Padding="Padding.Is3" Margin="Margin.Is3" Flex="Flex.Grow.Is1">
            <Heading Size="HeadingSize.Is4" Margin="Margin.Is3.FromBottom">Basket</Heading>
        </DropZone>
        <DropZone TItem="DropItem" Name="Fruit" DropAllowed="@((item) => item.Fruit)" Border="Border.Rounded" Background="Background.Light" Padding="Padding.Is3" Margin="Margin.Is3" Flex="Flex.Grow.Is1">
            <Heading Size="HeadingSize.Is4" Margin="Margin.Is3.FromBottom">Fruit</Heading>
        </DropZone>
        <DropZone TItem="DropItem" Name="Vegetable" DropAllowed="@((item) => !item.Fruit)" Border="Border.Rounded" Background="Background.Light" Padding="Padding.Is3" Margin="Margin.Is3" Flex="Flex.Grow.Is1">
            <Heading Size="HeadingSize.Is4" Margin="Margin.Is3.FromBottom">Vegetable</Heading>
        </DropZone>
    </ChildContent>
    <ItemTemplate>
        <Card Shadow="Shadow.Default" Margin="Margin.Is3.OnY">
            <CardBody>
                <Image Source="@context.Image" Text="DragDrop image example" Style="width:48px;height:48px;" />
                @context.Name
            </CardBody>
        </Card>
    </ItemTemplate>
</DropContainer>
```

```
@code {
    public class DropItem
    {
        public string Name { get; init; }

        public string Group { get; set; }

        public string Image { get; set; }

        public bool Fruit { get; set; }
    }

    private List<DropItem> items = new()
    {
        new DropItem() { Name = "Apple", Group = "Basket", Image = "img/fruit/apple.png", Fruit = true },
        new DropItem() { Name = "Bananas", Group = "Basket", Image = "img/fruit/bananas.png", Fruit = true },
        new DropItem() { Name = "Lemon", Group = "Fruit", Image = "img/fruit/lemon.png", Fruit = true },
        new DropItem() { Name = "Broccoli", Group = "Basket", Image = "img/fruit/broccoli.png" },
        new DropItem() { Name = "Strawberry", Group = "Fruit", Image = "img/fruit/strawberry.png", Fruit = true },
        new DropItem() { Name = "Cherry", Group = "Basket", Image = "img/fruit/cherry.png", Fruit = true },
        new DropItem() { Name = "Cabbage", Group = "Vegetable", Image = "img/fruit/cabbage.png" },
    };

    private Task ItemDropped( DraggableDroppedEventArgs<DropItem> dropItem )
    {
        dropItem.Item.Group = dropItem.DropZoneName;
        return Task.CompletedTask;
    }
}
```

### Reorder items

Items can be reordered inside each dropzone with the AllowReorder bool set to true on the dropzone.
            The Reordered function triggers each time the order changes or items are added or removed from the dropzone, providing the current order in a dictionary.

#### Drop Zone 1

Item 1

Item 2

Item 3

#### Drop Zone 2

Item 4

Item 5

#### Drop Zone 3

```
<DropContainer TItem="DropItem" Items="@items" ItemsFilter="@((item, dropZone) => item.Group == dropZone)" ItemDropped="@ItemDropped" Flex="Flex.Wrap.Grow.Is1">
    <ChildContent>
        @for ( int i = 1; i < 4; i++ )
        {
            var dropzone = i.ToString();

            <DropZone TItem="DropItem" Name="@dropzone" AllowReorder Reordered="@Reordered" Padding="Padding.Is3" Margin="Margin.Is3" Flex="Flex.Grow.Is1">
                <Heading Size="HeadingSize.Is4" Margin="Margin.Is3.FromBottom">Drop Zone @dropzone</Heading>
            </DropZone>
        }
    </ChildContent>
    <ItemTemplate>
        <Card Shadow="Shadow.Default" Margin="Margin.Is3.OnY">
            <CardBody>
                @context.Name
            </CardBody>
        </Card>
    </ItemTemplate>
</DropContainer>

<Div >
    @reorderStatus
</Div>
```

```
@code {
    public class DropItem
    {
        public string Name { get; init; }

        public string Group { get; set; }
    }

    private List<DropItem> items = new()
    {
        new DropItem() { Name = "Item 1", Group = "1" },
        new DropItem() { Name = "Item 2", Group = "1" },
        new DropItem() { Name = "Item 3", Group = "1" },
        new DropItem() { Name = "Item 4", Group = "2" },
        new DropItem() { Name = "Item 5", Group = "2" },
    };

    private Task ItemDropped( DraggableDroppedEventArgs<DropItem> dropItem )
    {
        dropItem.Item.Group = dropItem.DropZoneName;
        return Task.CompletedTask;
    }

    string reorderStatus = "";
    
    private Task Reordered( DropZoneOrder<DropItem> order )
    {
        reorderStatus = $"Order in dropzone {order.DestinationDropZoneName}: {string.Join( ", ", order.OrderedItems.OrderBy( x => x.Order ).Select( x => x.Item.Name ) )}";
        return Task.CompletedTask;
    }
}
```

## API

### Parameters

#### DropContainer

| Parameter                     | Description                                                                                                                                   | Type                  | Default   |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------|
| ApplyDropClassesOnDragStarted | When true, DropContainer.DropAllowedClass or DropContainer.DropNotAllowedClass drop classes are applied as soon as a transaction has started. | bool                  | false     |
| ChildContent                  | Specifies the content to be rendered inside this DropContainer.                                                                               | RenderFragment        | null      |
| DisabledClass                 | Classname that is applied to the dropzone if the result of DropContainer.ItemDisabled is false.                                               | string                |           |
| DraggingClass                 | Classname that is applied to the dropzone when the drag operation has started.                                                                | string                |           |
| DropAllowedClass              | Classname that is applied if dropping to the current zone is allowed.                                                                         | string                |           |
| DropNotAllowedClass           | Classname that is applied if dropping to the current zone is not allowed.                                                                     | string                |           |
| ItemDraggingClass             | Classname that is applied to the drag item when it is being dragged.                                                                          | string                |           |
| Items                         | Items that are used for the drag&drop withing the container.                                                                                  | IEnumerable<TItem>    | null      |
| ItemTemplate                  | The render method that is used to render the items withing the dropzone.                                                                      | RenderFragment<TItem> | null      |

#### DropZone

| Parameter                     | Description                                                                                                                         | Type                  | Default   |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------|
| AllowReorder                  | If true, the reordering of the items will be enabled.                                                                               | bool                  | false     |
| ApplyDropClassesOnDragStarted | When true, DropZone.DropAllowedClass or DropZone.DropNotAllowedClass drop classes are applied as soon as a transaction has started. | bool?                 | null      |
| ChildContent                  | Specifies the content to be rendered inside this DropZone.                                                                          | RenderFragment        | null      |
| DisabledClass                 | Classname that is applied to the dropzone if the result of DropZone.ItemDisabled is false.                                          | string                |           |
| DraggingClass                 | Classname that is applied to the dropzone when the drag operation has started.                                                      | string                |           |
| DropAllowedClass              | Classname that is applied if dropping to the current zone is allowed.                                                               | string                |           |
| DropNotAllowedClass           | Classname that is applied if dropping to the current zone is not allowed.                                                           | string                |           |
| ItemDraggingClass             | Classname that is applied to the drag item when it is being dragged.                                                                | string                |           |
| ItemTemplate                  | The render method that is used to render the items withing the dropzone.                                                            | RenderFragment<TItem> | null      |
| Name                          | Gets or sets the unique name of the dropzone.                                                                                       | string                |           |
| OnlyZone                      | If true, will only act as a dropable zone and not render any items.                                                                 | bool                  | false     |

### Events

#### DropContainer

| Event        | Description                                                                                                                   | Type                                            |
|--------------|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| DropAllowed  | Determines if the item is allowed to be dropped to the specified zone.                                                        | Func<TItem, string, bool>                       |
| ItemDisabled | Determines if the item is disabled for dragging and dropping.                                                                 | Func<TItem, bool>                               |
| ItemDropped  | Callback that indicates that an item has been dropped on a drop zone. Should be used to update the "status" of the data item. | EventCallback<DraggableDroppedEventArgs<TItem>> |
| ItemsFilter  | The method used to determine if the item belongs to the dropzone.                                                             | Func<TItem, string, bool>                       |

#### DropZone

| Event        | Description                                                                                            | Type                             |
|--------------|--------------------------------------------------------------------------------------------------------|----------------------------------|
| DropAllowed  | Determines if the item is allowed to be dropped to this zone.                                          | Func<TItem, bool>                |
| ItemDisabled | Determines if the item is disabled for dragging and dropping.                                          | Func<TItem, bool>                |
| ItemsFilter  | The method used to determine if the item belongs to the dropzone.                                      | Func<TItem, bool>                |
| Reordered    | The callback that is raised when the order of items changed. Only if DropZone.AllowReorder is enabled. | Func<DropZoneOrder<TItem>, Task> |

### Methods

#### DropContainer

| Method                            | Description                                                                          | Return   | Parameters                                                                                      |
|-----------------------------------|--------------------------------------------------------------------------------------|----------|-------------------------------------------------------------------------------------------------|
| StartTransaction                  | Starts the new drag & drop transaction for the specified item and dropzone.          | void     | TItem item, string sourceZoneName, int draggableIndex, Func<Task> commited, Func<Task> canceled |
| CommitTransaction                 | Commits the drag & drop transaction.                                                 | Task     | string dropZoneName, bool reorderIsAllowed                                                      |
| CancelTransaction                 | Cancels the drag & drop transaction.                                                 | Task     |                                                                                                 |
| UpdateTransactionIndex            | Updates the draggable index for the current transaction.                             | void     | int index                                                                                       |
| GetTransactionItem                | Gets the item that is currently in the transaction.                                  | TItem    |                                                                                                 |
| Refresh                           | Request the refresh of the drag container.                                           | void     |                                                                                                 |
| GetTransactionIndex               | Gets the current transaction index.                                                  | int      |                                                                                                 |
| IsOrigin                          | Indicates if the supplied name and transaction index are in the current transaction. | bool     | int index, string zoneName                                                                      |
| IsTransactionOriginatedFromInside | Gets the name of the zone where the transaction has started.                         | bool     | string zoneName                                                                                 |

###### On this page

#### 

## 