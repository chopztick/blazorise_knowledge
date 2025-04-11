# Blazorise Offcanvas component

Blazorise Offcanvas component allows to build hidden sidebars into your project for navigation, shopping carts.

Offcanvas is a sidebar component that can be toggled to appear from the start, end, top, or bottom edge of the viewport.

- &lt; Offcanvas&gt; the main container.
- &lt;Offcanvas&gt; the main container.
    - &lt;OffcanvasHeader&gt;, a main offcanvas header.
    - &lt;OffcanvasBody&gt;, a main content of the offcanvas.
    - &lt;OffcanvasFooter&gt;, a main offcanvas footer.

## Examples

### Start Placement

The Offcanvas with the start placement appears from the beginning of the screen.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop Placement="Placement.Start">
    <OffcanvasHeader>
        Offcanvas Start
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        Offcanvas Content
    </OffcanvasBody>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas Start</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        return offcanvasRef.Hide();
    }
}
```

### Top Placement

The Offcanvas with the top placement appears from the top of the screen.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop Placement="Placement.Top">
    <OffcanvasHeader>
        Offcanvas Top
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        Offcanvas Content
    </OffcanvasBody>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas Top</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        return offcanvasRef.Hide();
    }
}
```

### Bottom Placement

The Offcanvas with the bottom placement appears from the bottom of the screen.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop Placement="Placement.Bottom">
    <OffcanvasHeader>
        Offcanvas Bottom
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        Offcanvas Content
    </OffcanvasBody>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas Bottom</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        return offcanvasRef.Hide();
    }
}
```

### End Placement

The Offcanvas with the end placement appears from the end of the screen.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop Placement="Placement.End">
    <OffcanvasHeader>
        Offcanvas End
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        Offcanvas Content
    </OffcanvasBody>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas End</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        return offcanvasRef.Hide();
    }
}
```

### Closing

If you want to prevent modal from closing you can use  event.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop Closing="@OnOffcanvasClosing">
    <OffcanvasHeader>
        Offcanvas Start
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        <Div Padding="Padding.Is3">
             Offcanvas Content
        </Div>
        <Div Padding="Padding.Is3">
             <Button Color="Color.Secondary" Clicked="@HideOffcanvas">This will close the offcanvas</Button>
             <Button Color="Color.Primary" Clicked="@TryHideOffcanvas">This will not</Button>
        </Div>
    </OffcanvasBody>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas Start</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private bool cancelClose;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        cancelClose = false;

        return offcanvasRef.Hide();
    }

    private Task TryHideOffcanvas()
    {
        cancelClose = true;

        return offcanvasRef.Hide();
    }

    private Task OnOffcanvasClosing( OffcanvasClosingEventArgs e )
    {
        // just set Cancel to prevent offcanvas from closing
        e.Cancel = cancelClose
            || e.CloseReason != CloseReason.UserClosing;

        return Task.CompletedTask;
    }
}
```

### Footer

To show a footer in the Offcanvas just add an  component.

Offcanvas Content

```
<Offcanvas @ref="offcanvasRef" ShowBackdrop>
    <OffcanvasHeader>
        Offcanvas Start
        <CloseButton Clicked="@HideOffcanvas" />
    </OffcanvasHeader>
    <OffcanvasBody>
        Offcanvas Content
    </OffcanvasBody>
    <OffcanvasFooter>
        <Button Color="Color.Primary" Clicked="@HideOffcanvas">Close Offcanvas</Button>
    </OffcanvasFooter>
</Offcanvas>

<Button Color="Color.Primary" Clicked="@ShowOffcanvas">Show Offcanvas</Button>
```

```
@code {
    private Offcanvas offcanvasRef;

    private Task ShowOffcanvas()
    {
        return offcanvasRef.Show();
    }

    private Task HideOffcanvas()
    {
        return offcanvasRef.Hide();
    }
}
```

## API

### Parameters

#### Offcanvas

| Parameter         | Description                                                                     | Type           | Default         |
|-------------------|---------------------------------------------------------------------------------|----------------|-----------------|
| Animated          | Specifies whether the Offcanvas should have an animated transition.             | bool           | true            |
| AnimationDuration | The duration of the animation in milliseconds.                                  | int            | 300             |
| ChildContent      | The content to be rendered inside the Offcanvas.                                | RenderFragment | null            |
| Placement         | Specifies the position of the Offcanvas.Possible values:Top, Bottom, Start, End | Placement      | Placement.Start |
| ShowBackdrop      | Specifies whether to render the backdrop for this Offcanvas.                    | bool           | true            |
| Visible           | Gets or sets the visibility state of the Offcanvas.                             | bool           | false           |

#### OffcanvasHeader

| Parameter    | Description                                                       | Type           | Default   |
|--------------|-------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this OffcanvasHeader. | RenderFragment | null      |

#### OffcanvasBody

| Parameter    | Description                                                     | Type           | Default   |
|--------------|-----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this OffcanvasBody. | RenderFragment | null      |

#### OffcanvasFooter

| Parameter    | Description                                                       | Type           | Default   |
|--------------|-------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this OffcanvasFooter. | RenderFragment | null      |

### Events

#### Offcanvas

| Event          | Description                                                            | Type                                  |
|----------------|------------------------------------------------------------------------|---------------------------------------|
| Closed         | Event callback for when the Offcanvas has been closed.                 | EventCallback                         |
| Closing        | Callback for handling the closing of the Offcanvas.                    | Func<OffcanvasClosingEventArgs, Task> |
| Opened         | Event callback for when the Offcanvas has been opened.                 | EventCallback                         |
| Opening        | Callback for handling the opening of the Offcanvas.                    | Func<OffcanvasOpeningEventArgs, Task> |
| VisibleChanged | Event callback for when the visibility state of the Offcanvas changes. | EventCallback<bool>                   |

### Methods

#### Offcanvas

| Method        | Description                                            | Return     | Parameters                                                     |
|---------------|--------------------------------------------------------|------------|----------------------------------------------------------------|
| Show          | Starts the offcanvas opening process.                  | Task       |                                                                |
| Hide          | Fires the offcanvas dialog closure process.            | Task       |                                                                |
| IsSafeToClose | Finds if the closable component is ready to be closed. | Task<bool> | string elementId, CloseReason closeReason, bool isChildClicked |
| Close         | Triggers the closable component to be closed.          | Task       | CloseReason closeReason                                        |

###### On this page

#### 

## 