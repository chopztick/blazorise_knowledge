# Blazorise Repeater component

The repeater component is a helper component that repeats the child content for each element in a collection.

One advantage over using traditional @foreach loop is that repeater have a full support for
    INotifyCollectionChanged. Meaning you can do custom actions whenever a data-source changes.

## Examples

### Basic

- 1
- 2
- 3
- 4

```
<UnorderedList>
    <Repeater Items="@items" CollectionChanged="@OnCollectionChanged">
        <UnorderedListItem style="@GetColor( context )">@context</UnorderedListItem>
    </Repeater>
</UnorderedList>
```

```
@code{
    System.Collections.ObjectModel.ObservableCollection<int> items { get; } = new( Enumerable.Range( 1, 4 ) );

    Task OnCollectionChanged( System.Collections.Specialized.NotifyCollectionChangedEventArgs eventArgs )
    {
        // do something

        return Task.CompletedTask;
    }

    private static string GetColor( int number )
    {
        const string letters = "0123456789ABCDEF";

        var color = "";

        for ( var i = 0; i < 6; i++ )
        {
            color += letters[( 3 * number + i ) % letters.Length];
        }

        return $"color: #{color}";
    }
}
```

## API

### Parameters

| Parameter    | Description                                                                                            | Type                  | Default   |
|--------------|--------------------------------------------------------------------------------------------------------|-----------------------|-----------|
| ChildContent | The content to render per item.                                                                        | RenderFragment<TItem> | null      |
| Items        | The items to render. When this is INotifyCollectionChanged it will hookup collection change listeners. | IEnumerable<TItem>    | null      |
| Skip         | [Optional] The number of items to skip.                                                                | long?                 | null      |
| Take         | [Optional] The number of items to take.                                                                | long?                 | null      |

### Events

| Event             | Description                                    | Type                                            |
|-------------------|------------------------------------------------|-------------------------------------------------|
| CollectionChanged | Occurs when Repeater.Items collection changes. | EventCallback<NotifyCollectionChangedEventArgs> |

### Methods

| Method             | Description                                                               | Return   | Parameters               |
|--------------------|---------------------------------------------------------------------------|----------|--------------------------|
| Attach             | Attaches the component to a Microsoft.AspNetCore.Components.RenderHandle. | void     | RenderHandle handle      |
| SetParametersAsync | Sets parameters supplied by the component's parent in the render tree.                     Remarks The Microsoft.AspNetCore.Components.IComponent.SetParametersAsync(Microsoft.AspNetCore.Components.ParameterView) method should be passed the entire set of parameter values each             time Microsoft.AspNetCore.Components.IComponent.SetParametersAsync(Microsoft.AspNetCore.Components.ParameterView) is called. It not required that the caller supply a parameter             value for all parameters that are logically understood by the component.                                                                           | Task     | ParameterView parameters |
| RenderItems        | Renders the items in the collection.                                      | void     |                          |

###### On this page

#### 

## 