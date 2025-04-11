# Blazorise ListGroup component

List groups are a flexible and powerful component for displaying a series of content.

List groups are a flexible and powerful component for displaying a series of content.
    Modify and extend them to support just about any content within.

- &lt; ListGroup&gt; the main container.
- &lt;ListGroup&gt; the main container.
    - &lt;ListGroupItem&gt; the list group item, can be selectable or not.

## Examples

### Basic

The most basic list group is an unordered list with list items and the proper classes.
        Build upon it with the options that follow, or with your own CSS as needed.

- An item
- A second item
- A third item
- A fourth item
- A disabled item

```
<ListGroup>
    <ListGroupItem>An item</ListGroupItem>
    <ListGroupItem>A second item</ListGroupItem>
    <ListGroupItem>A third item</ListGroupItem>
    <ListGroupItem>A fourth item</ListGroupItem>
    <ListGroupItem Disabled>A disabled item</ListGroupItem>
</ListGroup>
```

### Selectable items

Add  to indicate the current active selection.

- An item
- A second item
- A third item
- A fourth item
- A disabled item

```
<ListGroup Mode="ListGroupMode.Selectable" @bind-SelectedItem="selectedItem">
    <ListGroupItem Name="first">An item</ListGroupItem>
    <ListGroupItem Name="second">A second item</ListGroupItem>
    <ListGroupItem Name="third">A third item</ListGroupItem>
    <ListGroupItem Name="fourth">A fourth item</ListGroupItem>
    <ListGroupItem Name="fifth" Disabled>A disabled item</ListGroupItem>
</ListGroup>
```

```
@code {
    private string selectedItem = "first";
}
```

### Flush

Add  to remove some borders and rounded corners to render list group items edge-to-edge
        in a parent container (e.g., cards).

- An item
- A second item
- A third item
- A fourth item
- A disabled item

```
<ListGroup Flush>
    <ListGroupItem>An item</ListGroupItem>
    <ListGroupItem>A second item</ListGroupItem>
    <ListGroupItem>A third item</ListGroupItem>
    <ListGroupItem>A fourth item</ListGroupItem>
    <ListGroupItem Disabled>A disabled item</ListGroupItem>
</ListGroup>
```

### Contextual colors

Use contextual utilities to style list items with a stateful background and color.

- Default
- Primary
- Secondary
- Success
- Danger
- Warning
- Info
- Light
- Dark

```
<ListGroup>
    <ListGroupItem Color="Color.Default">Default</ListGroupItem>
    <ListGroupItem Color="Color.Primary">Primary</ListGroupItem>
    <ListGroupItem Color="Color.Secondary">Secondary</ListGroupItem>
    <ListGroupItem Color="Color.Success">Success</ListGroupItem>
    <ListGroupItem Color="Color.Danger">Danger</ListGroupItem>
    <ListGroupItem Color="Color.Warning">Warning</ListGroupItem>
    <ListGroupItem Color="Color.Info">Info</ListGroupItem>
    <ListGroupItem Color="Color.Light">Light</ListGroupItem>
    <ListGroupItem Color="Color.Dark">Dark</ListGroupItem>
</ListGroup>
```

Contextual classes also work with  items. Note the addition of the hover styles
        here not present in the previous example. Also supported is the active state; apply it to indicate an
         selection on a contextual list group item.

- Default
- Primary
- Secondary
- Success
- Danger
- Warning
- Info
- Light
- Dark

```
<ListGroup Mode="ListGroupMode.Selectable">
    <ListGroupItem Name="none" Color="Color.Default">Default</ListGroupItem>
    <ListGroupItem Name="primary" Color="Color.Primary">Primary</ListGroupItem>
    <ListGroupItem Name="secondary" Color="Color.Secondary">Secondary</ListGroupItem>
    <ListGroupItem Name="success" Color="Color.Success">Success</ListGroupItem>
    <ListGroupItem Name="danger" Color="Color.Danger">Danger</ListGroupItem>
    <ListGroupItem Name="warning" Color="Color.Warning">Warning</ListGroupItem>
    <ListGroupItem Name="info" Color="Color.Info">Info</ListGroupItem>
    <ListGroupItem Name="light" Color="Color.Light">Light</ListGroupItem>
    <ListGroupItem Name="dark" Color="Color.Dark">Dark</ListGroupItem>
</ListGroup>
```

### With badges

Add badges to any list group item to show unread counts, activity, and more with the help of some utilities.

- A list item
        14
- A second list item
        2
- A third list item
        1

```
<ListGroup Flush>
    <ListGroupItem Flex="Flex.JustifyContent.Between.AlignItems.Center">
        A list item
        <Badge Color="Color.Primary" Pill>14</Badge>
    </ListGroupItem>
    <ListGroupItem Flex="Flex.JustifyContent.Between.AlignItems.Center">
        A second list item
        <Badge Color="Color.Primary" Pill>2</Badge>
    </ListGroupItem>
    <ListGroupItem Flex="Flex.JustifyContent.Between.AlignItems.Center">
        A third list item
        <Badge Color="Color.Primary" Pill>1</Badge>
    </ListGroupItem>
</ListGroup>
```

### Custom content

Add nearly any HTML within, even for linked list groups like the one below, with the help of flexbox utilities.

- List group item heading
3 days ago
Some placeholder content in a paragraph.
And some small print.
- List group item heading
3 days ago
Some placeholder content in a paragraph.
And some muted small print.
- List group item heading
3 days ago
Some placeholder content in a paragraph.
And some muted small print.

```
<ListGroup Flush>
    <ListGroupItem>
        <Div Flex="Flex.JustifyContent.Between" Width="Width.Is100">
            <Heading Size="HeadingSize.Is5" Margin="Margin.Is1.FromBottom">List group item heading</Heading>
            <Small>3 days ago</Small>
        </Div>
        <Paragraph Margin="Margin.Is1.FromBottom">Some placeholder content in a paragraph.</Paragraph>
        <Small>And some small print.</Small>
    </ListGroupItem>
    <ListGroupItem>
        <Div Flex="Flex.JustifyContent.Between" Width="Width.Is100">
            <Heading Size="HeadingSize.Is5" Margin="Margin.Is1.FromBottom">List group item heading</Heading>
            <Small TextColor="TextColor.Muted">3 days ago</Small>
        </Div>
        <Paragraph Margin="Margin.Is1.FromBottom">Some placeholder content in a paragraph.</Paragraph>
        <Small TextColor="TextColor.Muted">And some muted small print.</Small>
    </ListGroupItem>
    <ListGroupItem>
        <Div Flex="Flex.JustifyContent.Between" Width="Width.Is100">
            <Heading Size="HeadingSize.Is5" Margin="Margin.Is1.FromBottom">List group item heading</Heading>
            <Small TextColor="TextColor.Muted">3 days ago</Small>
        </Div>
        <Paragraph Margin="Margin.Is1.FromBottom">Some placeholder content in a paragraph.</Paragraph>
        <Small TextColor="TextColor.Muted">And some muted small print.</Small>
    </ListGroupItem>
</ListGroup>
```

## API

### Parameters

#### ListGroup

| Parameter     | Description                                                                                                          | Type                   | Default                       |
|---------------|----------------------------------------------------------------------------------------------------------------------|------------------------|-------------------------------|
| ChildContent  | Gets or sets the component child content.                                                                            | RenderFragment         | null                          |
| Flush         | Remove some borders and rounded corners to render list group items edge-to-edge in a parent container (e.g., cards). | bool                   | false                         |
| Mode          | Defines the list-group behavior mode.Possible values:Static, Selectable                                              | ListGroupMode          | ListGroupMode.Static          |
| Scrollable    | Makes the list group scrollable by adding a vertical scrollbar.                                                      | bool                   | false                         |
| SelectedItem  | Gets or sets currently selected item name.                                                                           | string                 |                               |
| SelectedItems | Gets or sets currently selected items names.                                                                         | List<string>           | null                          |
| SelectionMode | Defines the list-group selection mode.Possible values:Single, Multiple                                               | ListGroupSelectionMode | ListGroupSelectionMode.Single |

#### ListGroupItem

| Parameter    | Description                                                     | Type           | Default       |
|--------------|-----------------------------------------------------------------|----------------|---------------|
| ChildContent | Specifies the content to be rendered inside this ListGroupItem. | RenderFragment | null          |
| Color        | Gets or sets the list-group-item color.                         | Color          | Color.Default |
| Disabled     | Makes the item to make it appear disabled.                      | bool           | false         |
| Name         | Defines the item name.                                          | string         |               |

### Events

#### ListGroup

| Event                | Description                                               | Type                        |
|----------------------|-----------------------------------------------------------|-----------------------------|
| SelectedItemChanged  | An event raised when ListGroup.SelectedItem is changed.   | EventCallback<string>       |
| SelectedItemsChanged | An event raised when ListGroup.SelectedItems are changed. | EventCallback<List<string>> |

#### ListGroupItem

| Event   | Description                      | Type                          |
|---------|----------------------------------|-------------------------------|
| Clicked | Occurs when the item is clicked. | EventCallback<MouseEventArgs> |

### Methods

#### ListGroup

| Method     | Description                       | Return   | Parameters   |
|------------|-----------------------------------|----------|--------------|
| SelectItem | Sets the active item by the name. | Task     | string name  |

###### On this page

#### 

## 