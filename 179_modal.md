# Blazorise Modal component

Dialog is a small window that can be used to present information and user interface elements in an overlay.

The modal component provides a solid foundation for creating dialogs, popovers, lightboxes, or whatever else.

- &lt; Modal&gt; the main container.
- &lt;Modal&gt; the main container.
    - &lt; ModalContent&gt; a horizontally and vertically centered container, in which you can include any content.
    - &lt;ModalContent&gt; a horizontally and vertically centered container, in which you can include any content.
        - &lt; ModalHeader&gt; top part of the modal, usually contains a title and close button.
        - &lt;ModalHeader&gt; top part of the modal, usually contains a title and close button.
            - &lt;ModalTitle&gt; a title of the modal.
            - &lt;CloseButton&gt; a simple close button located in the top right corner.
        - &lt;ModalBody&gt; main part of the modal, holds the input fields, images, etc.
        - &lt;ModalFooter&gt; bottom part of the modal, usually contains the action buttons.

## Examples

### Basic

Place the modal markup somewhere at root of you component layout.
        



        To work with the modal you must use the reference to the Modal component.

#### Employee edit

```
<Button Color="Color.Primary" Clicked="@ShowModal">Show Modal</Button>

<Modal @ref="modalRef">
    <ModalContent Centered>
        <ModalHeader>
            <ModalTitle>Employee edit</ModalTitle>
            <CloseButton />
        </ModalHeader>
        <ModalBody>
            <Field>
                <FieldLabel>Name</FieldLabel>
                <TextEdit Placeholder="Enter name..." />
            </Field>
            <Field>
                <FieldLabel>Surname</FieldLabel>
                <TextEdit Placeholder="Enter surname..." />
            </Field>
        </ModalBody>
        <ModalFooter>
            <Button Color="Color.Secondary" Clicked="@HideModal">Close</Button>
            <Button Color="Color.Primary" Clicked="@HideModal">Save Changes</Button>
        </ModalFooter>
    </ModalContent>
</Modal>
```

```
@code{
    // reference to the modal component
    private Modal modalRef;

    private Task ShowModal()
    {
        return modalRef.Show();
    }

    private Task HideModal()
    {
        return modalRef.Hide();
    }
}
```

### Two-way binding

You can also control the  visibility by declaring the  state.

#### Employee edit

```
<Button Color="Color.Primary" Clicked="@ShowModal">Show Modal</Button>

<Span Margin="Margin.Is3.FromStart">Modal is visible: @modalVisible</Span>

<Modal @bind-Visible="@modalVisible">
    <ModalContent Centered>
        <ModalHeader>
            <ModalTitle>Employee edit</ModalTitle>
            <CloseButton />
        </ModalHeader>
        <ModalBody>
            <Field>
                <FieldLabel>Name</FieldLabel>
                <TextEdit Placeholder="Enter name..." />
            </Field>
            <Field>
                <FieldLabel>Surname</FieldLabel>
                <TextEdit Placeholder="Enter surname..." />
            </Field>
        </ModalBody>
        <ModalFooter>
            <Button Color="Color.Secondary" Clicked="@HideModal">Close</Button>
            <Button Color="Color.Primary" Clicked="@HideModal">Save Changes</Button>
        </ModalFooter>
    </ModalContent>
</Modal>
```

```
@code{
    private bool modalVisible;

    private Task ShowModal()
    {
        modalVisible = true;

        return Task.CompletedTask;
    }

    private Task HideModal()
    {
        modalVisible = false;

        return Task.CompletedTask;
    }
}
```

### Closing

If you want to prevent modal from closing you can use  event.

#### Closing modal

Click on the buttons to close the modal.

```
<Button Color="Color.Primary" Clicked="@ShowModal">Show Modal</Button>

<Modal @ref="modalRef" Closing="@OnModalClosing">
    <ModalContent Centered>
        <ModalHeader>
            <ModalTitle>Closing modal</ModalTitle>
        </ModalHeader>
        <ModalBody>
            Click on the buttons to close the modal.
        </ModalBody>
        <ModalFooter>
            <Button Color="Color.Secondary" Clicked="@CloseModal">This will close the modal</Button>
            <Button Color="Color.Primary" Clicked="@TryCloseModal">This will not</Button>
        </ModalFooter>
    </ModalContent>
</Modal>
```

```
@code {
    // reference to the modal component
    private Modal modalRef;

    private bool cancelClose;

    private Task ShowModal()
    {
        return modalRef.Show();
    }

    private Task CloseModal()
    {
        cancelClose = false;

        return modalRef.Hide();
    }

    private Task TryCloseModal()
    {
        cancelClose = true;

        return modalRef.Hide();
    }

    private Task OnModalClosing( ModalClosingEventArgs e )
    {
        // just set Cancel to prevent modal from closing
        e.Cancel = cancelClose 
            || e.CloseReason != CloseReason.UserClosing;

        return Task.CompletedTask;
    }
}
```

### Fullscreen

If the built-in sizes are not enough you can show the modal in fullscreen.

#### Employee edit

```
<Button Color="Color.Primary" Clicked="@ShowModal">Show Modal</Button>

<Modal @ref="modalRef">
    <ModalContent Size="ModalSize.Fullscreen">
        <ModalHeader>
            <ModalTitle>Employee edit</ModalTitle>
            <CloseButton />
        </ModalHeader>
        <ModalBody>
            <Field>
                <FieldLabel>Name</FieldLabel>
                <TextEdit Placeholder="Enter name..." />
            </Field>
            <Field>
                <FieldLabel>Surname</FieldLabel>
                <TextEdit Placeholder="Enter surname..." />
            </Field>
        </ModalBody>
        <ModalFooter>
            <Button Color="Color.Secondary" Clicked="@HideModal">Close</Button>
            <Button Color="Color.Primary" Clicked="@HideModal">Save Changes</Button>
        </ModalFooter>
    </ModalContent>
</Modal>
```

```
@code{
    // reference to the modal component
    private Modal modalRef;

    private Task ShowModal()
    {
        return modalRef.Show();
    }

    private Task HideModal()
    {
        return modalRef.Hide();
    }
}
```

## Best Practices

### Use Sparingly

Modal dialogs are disruptive by nature and should be used sparingly. Do not use them to communicate nonessential information, such as success messages like "Logged in", "Copied", etc. Instead, use Notifications when appropriate.

### Fullscreen Mode

When using the Fullscreen mode for the Modal component, it's crucial to be aware of how you structure your layout within the ModalBody.

If the ModalBody is wrapped within a container that has the CSS property 'display' set to 'block', this can cause issues with the overflow behavior in the Fullscreen mode. Specifically, the 'display: block' CSS property can interfere with the automatic adjustments that are applied to the Modal in Fullscreen mode.

#### Impact:

This interference could lead to the loss of smooth scrolling, content being cut off, or the display not fitting correctly within the viewport dimensions.

#### Solution:

To avoid such problems

Refrain from using 'display: block' style with containers within ModalBody when working in Fullscreen mode.
        

                As an alternative, consider using a container with the CSS property 'display' set to 'contents', eg. 'display: contents;'. This property value allows the container to behave as though it's replaced by its children. This way, you can ensure the structure and style of your content are compatible with the Fullscreen modal settings.

Please take this warning into consideration when implementing your Modals to ensure an optimal user experience and accurate content display.

## Functions

| Name   | Description             |
|--------|-------------------------|
| Show() | Open the modal dialog.  |
| Hide() | Close the modal dialog. |

## API

### Parameters

#### Modal

| Parameter         | Description                                                                                                    | Type            | Default                 |
|-------------------|----------------------------------------------------------------------------------------------------------------|-----------------|-------------------------|
| Animated          | Gets or sets whether the component has any animations.                                                         | bool            | true                    |
| AnimationDuration | Gets or sets the animation duration, in milliseconds.                                                          | int             | 150                     |
| ChildContent      | Specifies the content to be rendered inside this Modal.                                                        | RenderFragment  | null                    |
| FocusTrap         | Defines if the modal should keep the input focus at all times.                                                 | bool?           | null                    |
| RenderMode        | Defines how the modal content will be rendered.Possible values:Default, LazyLoad, LazyReload                   | ModalRenderMode | ModalRenderMode.Default |
| ScrollToTop       | If true modal will scroll to top when opened.                                                                  | bool            | true                    |
| ShowBackdrop      | Specifies the backdrop needs to be rendered for this Modal.                                                    | bool            | true                    |
| Visible           | Defines the visibility of modal dialog.Remarks The Modal.Visible parameter should only be used in .razor code. | bool            | false                   |

#### ModalContent

| Parameter    | Description                                                                                 | Type           | Default           |
|--------------|---------------------------------------------------------------------------------------------|----------------|-------------------|
| Centered     | Centers the modal vertically.                                                               | bool           | false             |
| ChildContent | Specifies the content to be rendered inside this ModalContent.                              | RenderFragment | null              |
| Scrollable   | Scrolls the modal content independent of the page itself.                                   | bool           | false             |
| Size         | Changes the size of the modal.Possible values:Default, Small, Large, ExtraLarge, Fullscreen | ModalSize      | ModalSize.Default |

#### ModalBody

| Parameter    | Description                                                        | Type           | Default   |
|--------------|--------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this ModalBody.        | RenderFragment | null      |
| MaxHeight    | Sets the maximum height of the modal body (in viewport size unit). | int?           | null      |

#### ModalTitle

| Parameter    | Description                                                              | Type           | Default         |
|--------------|--------------------------------------------------------------------------|----------------|-----------------|
| ChildContent | Specifies the content to be rendered inside this ModalTitle.             | RenderFragment | null            |
| Size         | Gets or sets the title size.Possible values:Is1, Is2, Is3, Is4, Is5, Is6 | HeadingSize    | HeadingSize.Is4 |

### Events

#### Modal

| Event          | Description                                     | Type                              |
|----------------|-------------------------------------------------|-----------------------------------|
| Closed         | Occurs after the modal has closed.              | EventCallback                     |
| Closing        | Occurs before the modal is closed.              | Func<ModalClosingEventArgs, Task> |
| Opened         | Occurs after the modal has opened.              | EventCallback                     |
| Opening        | Occurs before the modal is opened.              | Func<ModalOpeningEventArgs, Task> |
| VisibleChanged | Occurs when the modal visibility state changes. | EventCallback<bool>               |

### Methods

#### Modal

| Method        | Description                                            | Return     | Parameters                                                     |
|---------------|--------------------------------------------------------|------------|----------------------------------------------------------------|
| Show          | Starts the modal opening process.                      | Task       |                                                                |
| Hide          | Fires the modal dialog closure process.                | Task       |                                                                |
| IsSafeToClose | Finds if the closable component is ready to be closed. | Task<bool> | string elementId, CloseReason closeReason, bool isChildClicked |
| Close         | Triggers the closable component to be closed.          | Task       | CloseReason closeReason                                        |

###### On this page

#### 

## 