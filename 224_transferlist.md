# Blazorise Transfer List component

The TransferList component is a versatile control element in Blazor that facilitates transferring items between two lists within applications.

Transfer List components provide an intuitive way to move items between two lists. These components enhance the user experience and streamline tasks that involve item organization and categorization.

## Examples

### Multiple Selection Mode

In the multiple selection mode, users can transfer multiple items between two lists.

- Apple
- Banana
- Cherry
- Grapes
- Orange
- Pear
- Strawberry

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Multiple"
              Mode="ListGroupMode.Selectable"
              Scrollable=false
              ShowMoveAll=false
              ValueField="item => item"
              TextField="item => item">
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry" };
}
```

### Single Selection Mode

In the single selection mode, users can transfer one item at a time between two lists.

- Apple
- Banana
- Cherry
- Grapes
- Orange
- Pear
- Strawberry

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Single"
              Mode="ListGroupMode.Selectable"
              Scrollable=false
              ShowMoveAll=false
              ValueField="item => item"
              TextField="item => item">
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry" };
}
```

### Move All

You can enable the  parameter to display the  buttons. These buttons allow users to move all items to the opposite list.

- Apple
- Banana
- Cherry
- Grapes
- Orange
- Pear
- Strawberry

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Multiple"
              Mode="ListGroupMode.Selectable"
              Scrollable=false
              ShowMoveAll
              ValueField="item => item"
              TextField="item => item">
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry" };
}
```

### Bind Lists

You can bind to both lists. The  and  parameters track the items in the first and second lists, respectively.
        You may also provide the starting items for each list. If the opposite list is empty, the list will be populated with the remaining items.

- Cherry
- Strawberry

- Apple
- Banana
- Grapes
- Orange
- Pear

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Single"
              Mode="ListGroupMode.Selectable"
              Scrollable=false
              ShowMoveAll=false
              @bind-ItemsStart=@listStart
              @bind-ItemsEnd=@listEnd
              ValueField="item => item"
              TextField="item => item">
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry" };
    private List<string> listStart = new List<string> {"Cherry", "Strawberry" };
    private List<string> listEnd;

}
```

### Scrollable

If you have a large number of items, you can enable the  parameter to add a vertical scrollbar to the Transfer List. And control the maximum height by using the  parameter.

- Cherry
- Strawberry

- Apple
- Banana
- Grapes
- Orange
- Pear
- Watermelon
- Pineapple
- Mango
- Blueberry
- Raspberry
- Kiwi
- Peach
- Plum
- Pomegranate
- Coconut
- Lemon
- Lime
- Cantaloupe
- Honeydew
- Avocado
- Fig
- Guava
- Passion Fruit
- Papaya
- Apricot
- Cranberry
- Blackberry
- Currant
- Lychee
- Dragon Fruit
- Tangerine
- Nectarine
- Persimmon
- Star Fruit
- Quince
- Kumquat
- Elderberry

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Single"
              Mode="ListGroupMode.Selectable"
                Scrollable
               MaxHeight="500px"
               ShowMoveAll=false
               @bind-ItemsStart=@listStart
               @bind-ItemsEnd=@listEnd
               ValueField="item => item"
               TextField="item => item">
 </TransferList>
```

```
@code {
    private List<string> list = new List<string> {
        "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry",
        "Watermelon", "Pineapple", "Mango", "Blueberry", "Raspberry",
        "Kiwi", "Peach", "Plum", "Pomegranate", "Coconut", "Lemon",
        "Lime", "Cantaloupe", "Honeydew", "Avocado", "Fig", "Guava",
        "Passion Fruit", "Papaya", "Apricot", "Cranberry", "Blackberry",
        "Currant", "Lychee", "Dragon Fruit", "Tangerine", "Nectarine",
        "Persimmon", "Star Fruit", "Quince", "Kumquat", "Elderberry"
    };

    private List<string> listStart = new List<string> { "Cherry", "Strawberry" };
    private List<string> listEnd;

}
```

### Can Move

You may customize which of the items are able to be moved by utilizing the  and  parameters.

- Apple
- Banana
- Cherry
- Grapes
- Orange
- Pear
- Strawberry

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Single"
              Mode="ListGroupMode.Selectable"
              CanMoveToEnd="@(item => item != "Orange")"
              CanMoveToStart="@(item => item != "Strawberry" && item != "Cherry")"
              Scrollable=false
              ShowMoveAll
              ValueField="item => item"
              TextField="item => item">
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Banana", "Cherry", "Grapes", "Orange", "Pear", "Strawberry" };
}
```

### Customize

You may customize the look of each of the transfer list by utilizing the  and  parameters.

- Apple
- Bananas
- Lemon
- Broccoli
- Strawberry
- Cherry
- Cabbage

```
<TransferList TItem="string"
              Items="@list"
              SelectionMode="ListGroupSelectionMode.Single"
              Mode="ListGroupMode.Selectable"
              Scrollable
              ShowMoveAll=false
              ValueField="item => item"
              TextField="item => item">
    <ItemStartTemplate>
        @(transferListItemContent( context ))
    </ItemStartTemplate>
    <ItemEndTemplate>
        @(transferListItemContent( context ))
    </ItemEndTemplate>
</TransferList>
```

```
@code {
    private List<string> list = new List<string> { "Apple", "Bananas", "Lemon", "Broccoli", "Strawberry", "Cherry", "Cabbage" };
    private List<string> listStart = new List<string>() { "Cabbage", "Broccoli" };

    private RenderFragment<Blazorise.Components.ListView.ItemContext<string>> transferListItemContent => item => __builder =>
    {
        <Card Background=Background.Info Shadow="Shadow.Default">
            <CardBody>
                @{
                    var imageSource = $"img/fruit/{item.Value.ToLower()}.png";
                }
                <Image Source="@imageSource" Style="width:24px;height:24px;" Text="Small image" />
                @item.Value
            </CardBody>
        </Card>
    };
}
```

## API

### Parameters

| Parameter          | Description                                                                       | Type                               | Default    |
|--------------------|-----------------------------------------------------------------------------------|------------------------------------|------------|
| ItemEndTemplate    | Specifies the content to be rendered inside each item of the Components.ListView. | RenderFragment<ItemContext<TItem>> | null       |
| Items              | Gets or sets the items in the list.                                               | List<TItem>                        | null       |
| ItemsEnd           | Gets or sets the items in the end list.                                           | List<TItem>                        | null       |
| ItemsStart         | Gets or sets the items in the start list.                                         | List<TItem>                        | null       |
| ItemStartTemplate  | Specifies the content to be rendered inside each item of the Components.ListView. | RenderFragment<ItemContext<TItem>> | null       |
| MaxHeight          | Sets the TransferList MaxHeight.      Defaults to 300px.                          | string                             | "300px"    |
| Mode               | Defines the list-group behavior mode.Possible values:Static, Selectable           | ListGroupMode                      | Selectable |
| MoveButtonsColor   | Defines the color of the move buttons.                                            | Color                              | Primary    |
| Scrollable         | Makes the list group scrollable by adding a vertical scrollbar.                   | bool                               | true       |
| SelectedItemEnd    | Gets or sets item that is currently selected in the end list.                     | TItem                              | null       |
| SelectedItemsEnd   | Gets or sets items that are currently selected in the end list.                   | List<TItem>                        | null       |
| SelectedItemsStart | Gets or sets items that are currently selected in the start list.                 | List<TItem>                        | null       |
| SelectedItemStart  | Gets or sets item that is currently selected in the start list.                   | TItem                              | null       |
| SelectionMode      | Defines the list-group selection mode.Possible values:Single, Multiple            | ListGroupSelectionMode             | Single     |
| ShowMoveAll        | Enables the "Move All" Actions.                                                   | bool                               | true       |

### Events

| Event                     | Description                                                                 | Type                       |
|---------------------------|-----------------------------------------------------------------------------|----------------------------|
| CanMoveToEnd              | Whether the item may be moved to the End List.                              | Func<TItem, bool>          |
| CanMoveToStart            | Whether the item may be moved to the Start List.                            | Func<TItem, bool>          |
| ItemsEndChanged           | Gets or sets the event callback for changes in the end list.                | EventCallback<List<TItem>> |
| ItemsStartChanged         | Gets or sets the event callback for changes in the start list.              | EventCallback<List<TItem>> |
| SelectedItemEndChanged    | Gets or sets the event callback for changes in the end list.                | EventCallback<TItem>       |
| SelectedItemsEndChanged   | Gets or sets the event callback for changes to the items in the end list.   | EventCallback<List<TItem>> |
| SelectedItemsStartChanged | Gets or sets the event callback for changes to the items in the start list. | EventCallback<List<TItem>> |
| SelectedItemStartChanged  | Gets or sets the event callback for changes in the start list.              | EventCallback<TItem>       |
| TextField                 | Gets or sets the function to extract the text field from an item.           | Func<TItem, string>        |
| ValueField                | Gets or sets the function to extract the value field from an item.          | Func<TItem, string>        |

### Methods

| Method            | Description                                               | Return   | Parameters   |
|-------------------|-----------------------------------------------------------|----------|--------------|
| MoveSelectedEnd   | Moves selected items from the start list to the end list. | Task     |              |
| MoveSelectedStart | Moves selected items from the end list to the start list. | Task     |              |
| MoveAllEnd        | Moves all items from the start list to the end list.      | Task     |              |
| MoveAllStart      | Moves all items from the end list to the start list.      | Task     |              |

###### On this page

#### 

## 