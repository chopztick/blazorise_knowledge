# Blazorise Check component

Check allow the user to toggle an option on or off.

The &lt;Check&gt; component provides users the ability to choose between two distinct values. These are very similar to a switch and can be used in complex forms and checklists. You can use this to supply a way for the user to toggle an option.

### Check

Simple card

```
<Check TValue="bool">Check me out</Check>
```

### With name

This example showcases two Blazorise checkboxes linked to the same identifier, . Both checkboxes contribute to the same data field upon submission when included in a form. This setup is ideal for grouping related choices under one name but requires careful data handling to distinguish between the choices on the server side.

```
<Check TValue="bool" Name="@name">Check me out</Check>
<Check TValue="bool" Name="@name">Check me out too!</Check>
```

```
@code{
    string name = "CheckMeOut";
}
```

## Usage

### With bind attribute

```
<Check TValue="bool" @bind-Checked="@rememberMe">Remember Me</Check>
```

```
@code{
    bool rememberMe;
}
```

### With event

```
<Check TValue="bool" Checked="@rememberMe" CheckedChanged="@OnRememberMeChanged">Remember Me</Check>
```

```
@code{
    bool rememberMe;

    void OnRememberMeChanged( bool value )
    {
        rememberMe = value;
    }
}
```

## API

### Parameters

| Parameter         | Description                                                                                                                                                                                                 | Type                     | Default        |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|----------------|
| Autofocus         | Set's the focus to the component after the rendering is done.                                                                                                                                               | bool                     | false          |
| Checked           | Gets or sets the checked flag.                                                                                                                                                                              | TValue                   | null           |
| CheckedExpression | Gets or sets an expression that identifies the checked value.                                                                                                                                               | Expression<Func<TValue>> | null           |
| ChildContent      | Specifies the content to be rendered inside this Check.                                                                                                                                                     | RenderFragment           | null           |
| Cursor            | Defines the mouse cursor based on the behaviour by the current css framework.Possible values:Default, Pointer                                                                                               | Cursor                   | Cursor.Default |
| Disabled          | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                     | bool                     | false          |
| Feedback          | Placeholder for validation messages.                                                                                                                                                                        | RenderFragment           | null           |
| Indeterminate     | The indeterminate property can help you to achieve a 'check all' effect.                                                                                                                                    | bool?                    | null           |
| Inline            | Group checkboxes or radios on the same horizontal row.                                                                                                                                                      | bool                     | false          |
| Name              | Defines the name attribute of a checkbox.Remarks The name attribute is used to identify form data after it has been submitted to the server, or to reference form data using JavaScript on the client side. | string                   |                |
| ReadOnly          | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                | bool                     | false          |
| Size              | Sets the size of the input control.                                                                                                                                                                         | Size?                    | null           |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                               | int?                     | null           |

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