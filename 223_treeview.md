# Blazorise TreeView component

The TreeView component is a graphical control element that presents a hierarchical view of information.

📊 The Community License has a limitation of 100 nodes. Unlock full access to all features with
    
        our premium plans.

The TreeView component is a powerful and flexible way to display hierarchical data in a tree-like structure. It allows users to navigate through the tree and perform actions on the nodes, such as expanding or collapsing them, selecting them, or performing other operations.

## Features

Display hierarchical data in a tree structure.
        

            Expand or collapse nodes.
        

            Select single or multiple nodes (depending on the selection mode).
        

            Allow Node Items to be disabled for selection.
        

            Customize the appearance of the nodes using templates.
        

            Perform actions on the nodes, such as deleting them or performing some other operation.

## Installation

To install the Blazorise TreeView component, run the following command in the Package Manager Console:

```
Install-Package Blazorise.TreeView
```

Alternatively, you can install the package using the .NET Core CLI:

```
dotnet add package Blazorise.TreeView
```

### Configuration

Once the package is installed, you need to configure your Blazor project to use the TreeView component.

In your main \_Imports.razor add:

```
@using Blazorise.TreeView
```

### Static files

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.TreeView/blazorise.treeview.css" rel="stylesheet" />
```

### Basic example

A basic TreeView that aims to reproduce standard tree-view behavior.

```
<TreeView Nodes="Items"
          GetChildNodes="@(item => item.Children)"
          HasChildNodes="@(item => item.Children?.Any() == true)"
          @bind-SelectedNode="selectedNode"
          @bind-ExpandedNodes="expandedNodes">
    <NodeContent>
        <Icon Name="IconName.Folder" />
        @context.Text
    </NodeContent>
</TreeView>
```

```
@code{
    public class Item
    {
        public string Text { get; set; }
        public IEnumerable<Item> Children { get; set; }
    }

    IEnumerable<Item> Items = new[]
    {
        new Item { Text = "Item 1" },
        new Item
        {
            Text = "Item 2",
            Children = new []
            {
                new Item { Text = "Item 2.1" },
                new Item
                {
                    Text = "Item 2.2",
                    Children = new []
                    {
                        new Item { Text = "Item 2.2.1" },
                        new Item { Text = "Item 2.2.2" },
                        new Item { Text = "Item 2.2.3" },
                        new Item { Text = "Item 2.2.4" }
                    }
                },
                new Item { Text = "Item 2.3" },
                new Item { Text = "Item 2.4" }
            }
        },
        new Item { Text = "Item 3" },
    };

    IList<Item> expandedNodes = new List<Item>();
    Item selectedNode;
}
```

### Expanding and Collapsing Nodes

By default, all nodes are collapsed except for the root node(s). To expand a node, click on the triangle icon next to its label. To collapse a node, click on the triangle icon again. You can also programmatically expand or collapse nodes using the  and  property of the TreeView class.

```
<Button Color="Color.Primary" Clicked="@(()=>treeViewRef.ExpandAll())">Expand all</Button>
<Button Color="Color.Secondary" Clicked="@(()=>treeViewRef.CollapseAll())">Collapse all</Button>

<TreeView @ref="@treeViewRef" Nodes="Items" GetChildNodes="@(item => item.Children)" HasChildNodes="@(item => item.Children?.Any() == true)">
    <NodeContent>
        <Icon Name="IconName.Folder" />
        @context.Text
    </NodeContent>
</TreeView>
```

```
@code {
    TreeView<Item> treeViewRef;

    public class Item
    {
        public string Text { get; set; }
        public IEnumerable<Item> Children { get; set; }
    }

    IEnumerable<Item> Items = new[]
    {
        new Item { Text = "Item 1" },
        new Item
        {
            Text = "Item 2",
            Children = new []
            {
                new Item { Text = "Item 2.1" },
                new Item
                {
                    Text = "Item 2.2",
                    Children = new []
                    {
                        new Item { Text = "Item 2.2.1" },
                        new Item { Text = "Item 2.2.2" },
                        new Item { Text = "Item 2.2.3" },
                        new Item { Text = "Item 2.2.4" }
                    }
                },
                new Item { Text = "Item 2.3" },
                new Item { Text = "Item 2.4" }
            }
        },
        new Item { Text = "Item 3" },
    };
}
```

### Multiple selection

The TreeView component multiple selection mode, allows users to select multiple nodes at the same time. To enable this mode, set the SelectionMode property to Multiple. When this mode is enabled, each node in the TreeView will display a checkbox next to its label. Users can then select or deselect nodes by clicking on the checkboxes.

The selected nodes can be accessed through the SelectedNodes property, which returns a list of the selected nodes. You can also use the SelectedNodesChanged event to be notified when the selection changes.

```
<TreeView Nodes="Items"
          GetChildNodes="@(item => item.Children)"
          HasChildNodes="@(item => item.Children?.Any() == true)"
          SelectionMode="TreeViewSelectionMode.Multiple"
          @bind-SelectedNodes="selectedNodes">
    <NodeContent>
        <Icon Name="IconName.Folder" />
        @context.Text
    </NodeContent>
</TreeView>
```

```
@code {
    public class Item
    {
        public string Text { get; set; }
        public IEnumerable<Item> Children { get; set; }
    }

    IEnumerable<Item> Items = new[]
    {
        new Item { Text = "Item 1" },
        new Item
        {
            Text = "Item 2",
            Children = new []
            {
                new Item { Text = "Item 2.1" },
                new Item
                {
                    Text = "Item 2.2",
                    Children = new []
                    {
                        new Item { Text = "Item 2.2.1" },
                        new Item { Text = "Item 2.2.2" },
                        new Item { Text = "Item 2.2.3" },
                        new Item { Text = "Item 2.2.4" }
                    }
                },
                new Item { Text = "Item 2.3" },
                new Item { Text = "Item 2.4" }
            }
        },
        new Item { Text = "Item 3" },
    };

    IList<Item> selectedNodes = new List<Item>();
}
```

### Observable Lists

The Observable Lists feature in Blazorise TreeView component enables automatic updates and synchronization of the TreeView data with the underlying data source. This is achieved through the implementation of an observable pattern where the TreeView component listens to changes in the data source, and updates its visual representation accordingly.

When using Observable Lists in the Blazorise TreeView component, any modifications to the underlying data source, such as adding, removing, or updating nodes, will automatically trigger the necessary updates in the TreeView component. This ensures that the TreeView always reflects the most up-to-date state of the data.

It is of note that the Nodes parameter is a one way bound collection and as such, if you want to add and remove items, it is recommended that it is used as an ObservableCollection in order to keep the TreeView properly synced across refreshes.

```
@using System.Collections.ObjectModel;
@using Blazorise.Extensions

<Row>
    <Column>
        <Button Clicked="@OnAddNodeClick" Color="Color.Primary">Add node</Button>
        <Button Clicked="@OnRemoveNodeClick" Color="Color.Danger">Remove node</Button>
    </Column>
    <Column>
        <TreeView Nodes="Items"
                  GetChildNodes="@(item => item.Children)"
                  HasChildNodes="@(item => item.Children?.Any() == true)"
                  @bind-SelectedNode="selectedNode"
                  @bind-ExpandedNodes="expandedNodes">
            <NodeContent>
                <Icon Name="IconName.Folder" />
                @context.Text
            </NodeContent>
        </TreeView>
    </Column>
</Row>
```

```
@code {
    private Task OnAddNodeClick()
    {
        Items.Add( new Item { Text = $"Item {Items.Count + 1}" } );

        return Task.CompletedTask;
    }

    private async Task OnRemoveNodeClick()
    {
        if ( selectedNode is null )
            return;

        await RemoveItem( selectedNode );
    }

    public Task RemoveItem( Item item )
    {
        SearchTryRemoveItem( Items, item );
        return Task.CompletedTask;
    }

    private void SearchTryRemoveItem( ObservableCollection<Item> rows, Item item )
    {
        if ( rows.IsNullOrEmpty() )
            return;

        var nodeToRemove = rows.FirstOrDefault( x => x.Equals( item ) );

        if ( nodeToRemove is not null )
        {
            rows.Remove( nodeToRemove );
        }
        else
        {
            foreach ( var row in rows )
            {
                SearchTryRemoveItem( row.Children, item );
            }
        }
    }

    public class Item
    {
        public string Text { get; set; }
        public ObservableCollection<Item> Children { get; set; }
    }

    ObservableCollection<Item> Items = new()
    {
        new Item { Text = "Item 1" },
        new Item
        {
            Text = "Item 2",
            Children = new ObservableCollection<Item>()
            {
                new Item { Text = "Item 2.1" },
                new Item
                {
                    Text = "Item 2.2",
                    Children = new ObservableCollection<Item>()
                    {
                        new Item { Text = "Item 2.2.1" },
                        new Item { Text = "Item 2.2.2" },
                        new Item { Text = "Item 2.2.3" },
                        new Item { Text = "Item 2.2.4" }
                    }
                },
                new Item { Text = "Item 2.3" },
                new Item { Text = "Item 2.4" }
            }
        },
        new Item { Text = "Item 3" },
    };

    IList<Item> expandedNodes = new List<Item>();
    Item selectedNode;
}
```

### Node Context Menu

To integrate the context menu with the TreeView, you need to:

1. Use the TreeView NodeContextMenu event to get the current node and show the menu.
2. Use the context menu's MouseEventArgs parameter to handle the desired operation.

In this example, the context menu is used to show the menu items, put an item in edit mode and delete items.

```
@using System.Drawing

<TreeView TNode="Item"
          Nodes="Items"
          GetChildNodes="@(item => item.Children)"
          HasChildNodes="@(item => item.Children?.Any() == true)"
          AutoExpandAll
          @bind-SelectedNode="selectedNode"
          @bind-ExpandedNodes="expandedNodes"
          NodeContextMenu="@OnNodeContextMenu"
          NodeContextMenuPreventDefault>
    <NodeContent>
        <Icon Name="IconName.Folder" />
        @context.Text
    </NodeContent>
</TreeView>

@if ( showContextMenu )
{
    <Div Position="Position.Fixed" Background="Background.Danger" Style="@($"left:{contextMenuPosX}px; top:{contextMenuPosY}px;")">
        <ListGroup>
            <ListGroupItem>
                <Strong>Node: @contextMenuNode?.Text</Strong>
            </ListGroupItem>
            <ListGroupItem Clicked="@(()=>OnContextItemEditClicked(contextMenuNode))" Style="cursor: pointer;">
                <Icon Name="IconName.Edit" TextColor="TextColor.Secondary" /> Edit
            </ListGroupItem>
            <ListGroupItem Clicked="@(()=>OnContextItemDeleteClicked(contextMenuNode))" Style="cursor: pointer;">
                <Icon Name="IconName.Delete" TextColor="TextColor.Danger" /> Delete
            </ListGroupItem>
        </ListGroup>
    </Div>
}
```

```
@code {
    public class Item
    {
        public string Text { get; set; }
        public IEnumerable<Item> Children { get; set; }
    }

    IEnumerable<Item> Items = new[]
    {
        new Item { Text = "Item 1" },
        new Item
        {
            Text = "Item 2",
            Children = new []
            {
                new Item { Text = "Item 2.1" },
                new Item
                {
                    Text = "Item 2.2",
                    Children = new []
                    {
                        new Item { Text = "Item 2.2.1" },
                        new Item { Text = "Item 2.2.2" },
                        new Item { Text = "Item 2.2.3" },
                        new Item { Text = "Item 2.2.4" }
                    }
                },
                new Item { Text = "Item 2.3" },
                new Item { Text = "Item 2.4" }
            }
        },
        new Item { Text = "Item 3" },
    };

    IList<Item> expandedNodes = new List<Item>();
    Item selectedNode;

    bool showContextMenu = false;
    double contextMenuPosX;
    double contextMenuPosY;
    Item contextMenuNode;

    protected Task OnNodeContextMenu( TreeViewNodeMouseEventArgs<Item> eventArgs )
    {
        showContextMenu = true;
        contextMenuNode = eventArgs.Node;
        contextMenuPosX = eventArgs.MouseEventArgs.ClientX;
        contextMenuPosY = eventArgs.MouseEventArgs.ClientY;

        return Task.CompletedTask;
    }

    protected Task OnContextItemEditClicked( Item item )
    {
        showContextMenu = false;

        return Task.CompletedTask;
    }

    protected Task OnContextItemDeleteClicked( Item item )
    {
        showContextMenu = false;

        return Task.CompletedTask;
    }
}
```

### Virtualization

This example demonstrates how to use virtualization in a Blazorise &lt;TreeView&gt; component to efficiently render large hierarchical data sets. Virtualization improves performance by only rendering the visible nodes in the viewport, rather than all nodes in the tree. This is particularly useful when dealing with large numbers of nodes, as it reduces the DOM size and enhances responsiveness.

For virtualization to function correctly, it is essential to specify both the Height and Overflow properties

1. Height: Defines the fixed height of the TreeView component. Without a specified height, the tree would expand indefinitely, defeating the purpose of virtualization since all nodes would be rendered at once.
2. Overflow: Ensures that the tree's content is scrollable. This scrollable area allows for dynamic loading of nodes as the user scrolls, effectively utilizing virtualization to render only the nodes currently in view.

By default, when Virtualize is enabled, we will define Height and Overflow for you, if they are not already explicitly defined.

```
<TreeView Nodes="Items"
          GetChildNodes="@(item => item.Children)"
          HasChildNodes="@(item => item.Children?.Any() == true)"
          @bind-SelectedNode="selectedNode"
          @bind-ExpandedNodes="expandedNodes"
          Virtualize>
    <NodeContent>
        <Icon Name="IconName.Folder" />
        @context.Text
    </NodeContent>
</TreeView>
```

```
@code {
    public class Item
    {
        public string Text { get; set; }
        public IEnumerable<Item> Children { get; set; }
    }

    protected override void OnInitialized()
    {
        Items = Enumerable.Range( 1, 4 ).Select( rootIndex => new Item
        {
            Text = $"Root Node {rootIndex}",
            Children = Enumerable.Range( 1, 100 ).Select( childIndex => new Item
            {
                Text = $"Root {rootIndex} - Child {childIndex}",
                Children = Enumerable.Empty<Item>() // No children for the child nodes in this example
            } )
        } ).ToList();

        base.OnInitialized();
    }

    IEnumerable<Item> Items;

    IList<Item> expandedNodes = new List<Item>();
    Item selectedNode;
}
```

## API

### Parameters

| Parameter                     | Description                                                                                                                                                               | Type                  | Default                      |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|------------------------------|
| AutoExpandAll                 | Defines if the treenode should be automatically expanded. Note that it can happen only once when the tree is first loaded.                                                | bool                  | false                        |
| ChildContent                  | Specifies the content to be rendered inside this TreeView.TreeView.                                                                                                       | RenderFragment        | null                         |
| CollapseIconName              | Defines the name of the treenode collapse icon.                                                                                                                           | IconName              | ChevronDown                  |
| CollapseIconSize              | Defines the size of the treenode collapse icon.                                                                                                                           | IconSize?             | null                         |
| CollapseIconStyle             | Defines the style of the treenode collapse icon.                                                                                                                          | IconStyle?            | null                         |
| ExpandedNodes                 | List of currently expanded TreeView items (child nodes).                                                                                                                  | IList<TNode>          | new List<TNode>()            |
| ExpandIconName                | Defines the name of the treenode expand icon.                                                                                                                             | IconName              | ChevronRight                 |
| ExpandIconSize                | Defines the size of the treenode expand icon.                                                                                                                             | IconSize?             | null                         |
| ExpandIconStyle               | Defines the style of the treenode expand icon.                                                                                                                            | IconStyle?            | null                         |
| NodeContent                   | Template to display content for the node                                                                                                                                  | RenderFragment<TNode> | null                         |
| NodeContextMenuPreventDefault | Used to prevent the default action for a TreeView.TreeView.NodeContextMenu event.                                                                                         | bool                  | false                        |
| Nodes                         | Collection of child TreeView items (child nodes)                                                                                                                          | IEnumerable<TNode>    | null                         |
| SelectedNode                  | Currently selected TreeView item/node.                                                                                                                                    | TNode                 | null                         |
| SelectedNodes                 | Currently selected TreeView items/nodes.                                                                                                                                  | IList<TNode>          | null                         |
| SelectionMode                 | Defines the selection mode of the TreeView.TreeView.Possible values:Single, Multiple                                                                                      | TreeViewSelectionMode | TreeViewSelectionMode.Single |
| Virtualize                    | Controls if the child nodes, which are currently not expanded, are visible.     This is useful for optimizing large TreeViews. See Docs for virtualization for more info. | bool                  | false                        |

### Events

| Event                | Description                                                                 | Type                                             |
|----------------------|-----------------------------------------------------------------------------|--------------------------------------------------|
| DisabledNodeStyling  | Gets or sets disabled node styling.                                         | Action<TNode, NodeStyling>                       |
| ExpandedNodesChanged | Occurs when the collection of expanded nodes has changed.                   | EventCallback<IList<TNode>>                      |
| GetChildNodes        | Gets the list of child nodes for each node.                                 | Func<TNode, IEnumerable<TNode>>                  |
| GetChildNodesAsync   | Gets the list of child nodes for each node.                                 | Func<TNode, Task<IEnumerable<TNode>>>            |
| HasChildNodes        | Indicates if the node has child elements.                                   | Func<TNode, bool>                                |
| HasChildNodesAsync   | Indicates if the node has child elements.                                   | Func<TNode, Task<bool>>                          |
| IsDisabled           | Indicates the node's disabled state. Used for preventing selection.         | Func<TNode, bool>                                |
| NodeContextMenu      | The event is fired when the node is right clicked to show the context menu. | EventCallback<TreeViewNodeMouseEventArgs<TNode>> |
| NodeStyling          | Gets or sets node styling.                                                  | Action<TNode, NodeStyling>                       |
| SelectedNodeChanged  | Occurs when the selected TreeView node has changed.                         | EventCallback<TNode>                             |
| SelectedNodesChanged | Occurs when the selected TreeView nodes has changed.                        | EventCallback<IList<TNode>>                      |
| SelectedNodeStyling  | Gets or sets selected node styling.                                         | Action<TNode, NodeStyling>                       |

### Methods

| Method          | Description                                                            | Return   | Parameters   |
|-----------------|------------------------------------------------------------------------|----------|--------------|
| RemoveNode      | Attempts to find and remove an existing node from the Treeview.        | Task     | TNode node   |
| Reload          | Triggers the reload of the TreeView.TreeView.Nodes.                    | Task     |              |
| SelectNode      | Selects the node when in single selection mode.                        | void     | TNode node   |
| ToggleCheckNode | Toggles the checked state of the node when in multiple selection mode. | Task     | TNode node   |
| ExpandAll       | Expands all the collapsed TreeView nodes.                              | Task     |              |
| CollapseAll     | Collapses all the expanded TreeView nodes.                             | Task     |              |

###### On this page

#### 

## 