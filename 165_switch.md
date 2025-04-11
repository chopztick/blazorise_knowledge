# Blazorise Switch  component

Switch is used for switching between two opposing states.

The &lt;Switch&gt; component provides users the ability to choose between two distinct values. These are
    very similar to a toggle, or on/off switch, though aesthetically different than a checkbox.

Switches are the preferred way to adjust settings on mobile. The option that the switch controls,
    as well as the state it’s in, should be made clear from the corresponding inline label.

## Examples

### Basic

```
<Switch TValue="bool">Remember me</Switch>
```

## Binding

### Two-way binding

```
<Switch TValue="bool" @bind-Checked="@rememberMe">Remember Me</Switch>
```

```
@code{
    bool rememberMe;
}
```

### Manual event binding

```
<Switch TValue="bool" Checked="@rememberMe" CheckedChanged="@OnRememberMeChanged">Remember Me</Switch>
```

```
@code{
    bool rememberMe;

    Task OnRememberMeChanged( bool value )
    {
        rememberMe = value;

        return Task.CompletedTask;
    }
}
```

## API

### Parameters

| Parameter         | Description                                                                                                   | Type                     | Default        |
|-------------------|---------------------------------------------------------------------------------------------------------------|--------------------------|----------------|
| Autofocus         | Set's the focus to the component after the rendering is done.                                                 | bool                     | false          |
| Checked           | Gets or sets the checked flag.                                                                                | TValue                   | null           |
| CheckedExpression | Gets or sets an expression that identifies the checked value.                                                 | Expression<Func<TValue>> | null           |
| ChildContent      | Specifies the content to be rendered inside this Switch.                                                      | RenderFragment           | null           |
| Color             | Defines the switch named color.                                                                               | Color                    | Color.Default  |
| Cursor            | Defines the mouse cursor based on the behaviour by the current css framework.Possible values:Default, Pointer | Cursor                   | Cursor.Default |
| Disabled          | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                     | false          |
| Feedback          | Placeholder for validation messages.                                                                          | RenderFragment           | null           |
| Inline            | Group checkboxes or radios on the same horizontal row.                                                        | bool                     | false          |
| ReadOnly          | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                     | false          |
| Size              | Sets the size of the input control.                                                                           | Size?                    | null           |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                     | null           |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| CheckedChanged        | Occurs when the check state is changed.                                                                                                                                                                                                                                                | EventCallback<TValue>            |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 