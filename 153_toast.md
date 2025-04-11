# Blazorise Toast component

Push notifications to your visitors with a toast, a lightweight and easily customizable alert message.

Toasts are brief alerts made to resemble push notifications, which are more common on desktop and mobile devices. Since they are flexbox-built, they are simple to align and reposition.

## Overview

Things to know when using the toast component:

Toasts are opt-in for performance reasons, so you must initialize them yourself.
Toasts will automatically hide if you do not specify Autohide="false".
Toasts must be wrapped with a &lt;Toaster&gt; component to be properly placed on a screen.
Use the toast service provider to show toasts programmatically with minimal code.

## Examples

### Basic

We suggest using a header and body to promote predictable and extensible toasts. Toast headers use display: flex, which makes it simple to align content because of our flexbox and margin utilities.

Toasts have very little required markup and are as flexible as you need them to be. We at least demand that your "toasted" content be contained in a single element, and we highly recommend the inclusion of a dismiss button.

Hello, world! This is a toast message.

```
<Div Position="Position.Relative" Width="Width.Is100" Height="Height.Rem(20)">
    <Toaster PlacementStrategy="ToasterPlacementStrategy.Absolute">
        <Toast Visible Autohide="false">
            <ToastHeader>
                <Strong Margin="Margin.IsAuto.FromEnd">Blazorise</Strong>
                <Small>11 mins ago</Small>
                <CloseButton />
            </ToastHeader>
            <ToastBody>
                Hello, world! This is a toast message.
            </ToastBody>
        </Toast>
    </Toaster>
</Div>
```

### Live example

Click the button below to show a toast (positioned with our utilities in the lower right corner) that has been hidden by default.

Hello, world! This is a toast message.

```
<Button Color="Color.Primary" Clicked="@(() => toastVisible = true)">
    Show live toast
</Button>

<Toaster>
    <Toast @bind-Visible="@toastVisible">
        <ToastHeader>
            <Strong Margin="Margin.IsAuto.FromEnd">Blazorise</Strong>
            <Small>11 mins ago</Small>
            <CloseButton />
        </ToastHeader>
        <ToastBody>
            Hello, world! This is a toast message.
        </ToastBody>
    </Toast>
</Toaster>
```

```
@code {
    bool toastVisible = false;
}
```

### Placements

You can use one of the following modifiers to change placements of the toast.

Hello, world! This is a toast message.

Hello, world! This is a toast message.

Hello, world! This is a toast message.

Hello, world! This is a toast message.

```
<Div Position="Position.Relative" Width="Width.Is100" Height="Height.Rem(20)">
    @ToastRenderFragment( ToasterPlacement.TopStart )

    @ToastRenderFragment( ToasterPlacement.TopEnd )

    @ToastRenderFragment( ToasterPlacement.BottomStart )

    @ToastRenderFragment( ToasterPlacement.BottomEnd )
</Div>
```

```
@code {
    private RenderFragment ToastRenderFragment( ToasterPlacement placement ) => __builder =>
    {
        <Toaster Placement="@placement" PlacementStrategy="ToasterPlacementStrategy.Absolute">
            <Toast Visible Autohide="false">
                <ToastHeader>
                    <Strong Margin="Margin.IsAuto.FromEnd">Blazorise</Strong>
                    <Small>11 mins ago</Small>
                    <CloseButton />
                </ToastHeader>
                <ToastBody>
                    Hello, world! This is a toast message.
                </ToastBody>
            </Toast>
        </Toaster>
    };
}
```

## Best Practices

### Use Sparingly

Notifications are disruptive by design and should be used sparingly. Use fewer notifications by reserving them for more important information that may otherwise go unnoticed by the user.

Less urgent notifications can be provided through a link or drop-down in the application header or footer, instead of immediate notifications.

### Limit Content Length

Aim for one or two lines of content. Notifications should be brief and to the point. More information can be provided through an embedded link or Button.

### Toast Positions

Toasts can be dispatched to all four corners of a page. We do not recommend to use more than one position for toasts in an application because that could be disorienting for users. Pick one desired position and configure it in the Toaster.

## API

### Parameters

#### Toaster

| Parameter         | Description                                                                                                           | Type                     | Default                        |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------------------|
| ChildContent      | The content to be rendered inside the Toaster component.                                                              | RenderFragment           | null                           |
| Placement         | Specifies the position of the Toaster component.Possible values:Top, TopStart, TopEnd, Bottom, BottomStart, BottomEnd | ToasterPlacement         | ToasterPlacement.BottomEnd     |
| PlacementStrategy | Specifies the placement strategy of the Toaster component.Possible values:Fixed, Absolute                             | ToasterPlacementStrategy | ToasterPlacementStrategy.Fixed |

#### Toast

| Parameter         | Description                                                     | Type           | Default   |
|-------------------|-----------------------------------------------------------------|----------------|-----------|
| Animated          | Specifies whether the Toast should have an animated transition. | bool           | true      |
| AnimationDuration | The duration of the animation in milliseconds.                  | int            | 300       |
| Autohide          | Automatically hide the toast after the delay.                   | bool           | true      |
| AutohideDelay     | Delay in milliseconds before hiding the toast.                  | double         | 5000      |
| ChildContent      | The content to be rendered inside the Toast.                    | RenderFragment | null      |
| Visible           | Gets or sets the visibility state of the Toast.                 | bool           | false     |

### Events

#### Toast

| Event          | Description                                                        | Type                              |
|----------------|--------------------------------------------------------------------|-----------------------------------|
| Closed         | Event callback for when the Toast has been closed.                 | EventCallback                     |
| Closing        | Callback for handling the closing of the Toast.                    | Func<ToastClosingEventArgs, Task> |
| Opened         | Event callback for when the Toast has been opened.                 | EventCallback                     |
| Opening        | Callback for handling the opening of the Toast.                    | Func<ToastOpeningEventArgs, Task> |
| VisibleChanged | Event callback for when the visibility state of the Toast changes. | EventCallback<bool>               |

### Methods

#### Toast

| Method   | Description                              | Return   | Parameters              |
|----------|------------------------------------------|----------|-------------------------|
| Show     | Starts the toast opening process.        | Task     |                         |
| Hide     | Fires the toast dialog closure process.  | Task     |                         |
| Close    | Closes the toast with reason of closing. | Task     | CloseReason closeReason |

###### On this page

#### 

## 