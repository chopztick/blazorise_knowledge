# Blazorise FocusTrap component

Manages focus of the forms and its input elements.

TrapFocus is a component that manages focus for its descendants. This is useful when implementing overlays such as modal dialogs, which should not allow the focus to escape while open.

When Active="true" the trap is enabled, and pressing Tab or Shift+Tab will rotate focus within the inner focusable elements of the component.

## Examples

By default, the component moves the focus to its descendants as soon as it activated.

```
<Card>
    <CardBody>
        <Switch TValue="bool" @bind-Checked="@focusTrapActive">Active</Switch>
    </CardBody>
    <CardBody>
        <FocusTrap Active="@focusTrapActive">
            <Field Horizontal>
                <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is2.OnDesktop">First Name</FieldLabel>
                <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is10.OnDesktop">
                    <TextEdit Autofocus />
                </FieldBody>
            </Field>
            <Field Horizontal>
                <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is2.OnDesktop">Last Name</FieldLabel>
                <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is10.OnDesktop">
                    <TextEdit />
                </FieldBody>
            </Field>
            <Field Horizontal>
                <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is2.OnDesktop">Address</FieldLabel>
                <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is10.OnDesktop">
                    <TextEdit />
                </FieldBody>
            </Field>
        </FocusTrap>
    </CardBody>
</Card>
```

```
@code {
    bool focusTrapActive = false;
}
```

## API

### Parameters

| Parameter    | Description                                                   | Type           | Default   |
|--------------|---------------------------------------------------------------|----------------|-----------|
| Active       | If true the TAB focus will be activated.                      | bool           | false     |
| ChildContent | Gets or sets the reference to the parent FocusTrap component. | RenderFragment | null      |

### Methods

| Method                              | Description                                                                   | Return   | Parameters                             |
|-------------------------------------|-------------------------------------------------------------------------------|----------|----------------------------------------|
| SetFocus                            | Sets the focus trap.                                                          | Task     |                                        |
| NotifyFocusableComponentInitialized | Notifies the container component that its IFocusableComponent is initialized. | void     | IFocusableComponent focusableComponent |
| NotifyFocusableComponentRemoved     | Notifies the container component that its IFocusableComponent is removed.     | void     | IFocusableComponent focusableComponent |

###### On this page

#### 

## 