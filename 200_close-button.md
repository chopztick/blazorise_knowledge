# Blazorise CloseButton component

A generic close button for dismissing content like modals and alerts.

The &lt;CloseButton&gt; is a simple button that highlights to the user that a part of the current UI can be dismissed such as an Alert or a Modal.

When used in an Alert or a Modal the component will be closed automatically. If not inside one of these components the
    Clicked EventCallback must be set for it to be useful.

### Manual close

```
<Alert Visible="@visible">
    I can be closed!
    <CloseButton Clicked="@OnClicked" />
</Alert>
```

```
@code {
    bool visible = true;

    Task OnClicked()
    {
        visible = false;

        return Task.CompletedTask;
    }
}
```

### Auto close

```
<Alert @bind-Visible="@visible">
    I can be closed!
    <CloseButton AutoClose="true" />
</Alert>
```

```
@code {
    bool visible = true;
}
```

### With other components

```
@if ( visible )
{
    <Div>
        Now you see me...
        <CloseButton Clicked="@OnClicked" />
    </Div>
}
```

```
@code {
    bool visible = true;

    Task OnClicked()
    {
        visible = false;

        return Task.CompletedTask;
    }
}
```

## API

### Parameters

| Parameter    | Description                                                                                                           | Type           | Default   |
|--------------|-----------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| AutoClose    | If true, the parent Alert or Modal with be automatically closed     when CloseButton button is placed inside of them. | bool?          | null      |
| ChildContent | Specifies the content to be rendered inside this CloseButton.                                                         | RenderFragment | null      |
| Disabled     | Flag to indicate that the button is not responsive for user interaction.                                              | bool           | false     |

### Events

| Event   | Description                        | Type                          |
|---------|------------------------------------|-------------------------------|
| Clicked | Occurs when the button is clicked. | EventCallback<MouseEventArgs> |

###### On this page

#### 

## 