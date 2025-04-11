# Blazorise InputMask component

Input mask allows the user to input a value in a specific format while typing.

The &lt;InputMask&gt; helps the user with the input by ensuring a predefined format. This can be useful for dates, numerics, phone numbers, ...

- 9: numeric
- a: alphabetical
- *: alphanumeric

## Examples

### Basic Mask

To start you only need to define the  parameter.

```
<InputMask Mask="99-9999999" />
```

### With Alias

Instead of masking an input element, it is also possible to use the inputmask for formatting given values.

```
<InputMask Alias="datetime" InputFormat="dd/mm/yyyy" OutputFormat="ddmmyyyy" />
```

## Other examples

### With Placeholder

You can control the placeholder that will be used for the mask. The  will be used when the mask is not defined. And the  will be used when the mask is defined for extra information to the user about the valid input format.

```
<InputMask Mask="99-9999999" MaskPlaceholder="X" Placeholder="Please enter a valid ID" />
```

## API

### Parameters

| Parameter            | Description                                                                                                                                                                                                                                                           | Type                     | Default                                  |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|------------------------------------------|
| Alias                | With an alias, you can define a complex mask definition and call it by using an alias name.     So this is mainly to simplify the use of your masks. Some aliases found in the extensions are email,     currency, decimal, integer, date, DateTime, dd/mm/yyyy, etc. | string                   |                                          |
| Autofocus            | Set's the focus to the component after the rendering is done.                                                                                                                                                                                                         | bool                     | false                                    |
| AutoUnmask           | Automatically unmask the value when retrieved. Default: false.                                                                                                                                                                                                        | bool                     | false                                    |
| ChildContent         | Specifies the content to be rendered inside this InputMask.                                                                                                                                                                                                           | RenderFragment           | null                                     |
| ClearIncomplete      | Clear the incomplete input on blur. Default: false                                                                                                                                                                                                                    | bool                     | false                                    |
| ClearMaskOnLostFocus | Remove the empty mask on blur or when not empty remove the optional trailing part. Default: true                                                                                                                                                                      | bool                     | true                                     |
| Color                | Sets the input text color.                                                                                                                                                                                                                                            | Color                    | Color.Default                            |
| Debounce             | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                                                                         | bool?                    | null                                     |
| DebounceInterval     | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                                                                     | int?                     | null                                     |
| DecimalSeparator     | Define the decimal separator (numeric mode only).                                                                                                                                                                                                                     | string                   |                                          |
| Disabled             | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                                                               | bool                     | false                                    |
| Feedback             | Placeholder for validation messages.                                                                                                                                                                                                                                  | RenderFragment           | null                                     |
| GroupSeparator       | Define the group separator (numeric mode only).                                                                                                                                                                                                                       | string                   |                                          |
| Immediate            | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                                                                                  | bool?                    | null                                     |
| InputFormat          | Defines the input format when the InputMask.Alias is used.                                                                                                                                                                                                            | string                   |                                          |
| Mask                 | The mask to use for the input.                                                                                                                                                                                                                                        | string                   |                                          |
| MaskPlaceholder      | The placeholder that will be used for the mask.                                                                                                                                                                                                                       | string                   |                                          |
| Nullable             | Return nothing when the user hasn't entered anything. Default: false.                                                                                                                                                                                                 | bool                     | false                                    |
| NumericInput         | Numeric input direction. Keeps the caret at the end.                                                                                                                                                                                                                  | bool                     | false                                    |
| OutputFormat         | Defines the output format of the InputMask.Value when the InputMask.Alias is used.                                                                                                                                                                                    | string                   |                                          |
| Pattern              | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                                                                                                                                            | string                   |                                          |
| Placeholder          | Sets the placeholder for the empty text.                                                                                                                                                                                                                              | string                   |                                          |
| Plaintext            | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                                                                                                                  | bool                     | false                                    |
| PositionCaretOnClick | Defines the positioning of the caret on click.Possible values:None, LastValidPosition, RadixFocus, Select, Ignore                                                                                                                                                     | InputMaskCaretPosition   | InputMaskCaretPosition.LastValidPosition |
| ReadOnly             | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                                                                          | bool                     | false                                    |
| Regex                | Use a regular expression as a mask.                                                                                                                                                                                                                                   | string                   |                                          |
| RightAlign           | Align the input to the right.Remarks By setting the rightAlign you can specify to right-align an inputmask. This is only applied     in combination op the numericInput option or the dir-attribute. The default is true.                                             | bool                     | false                                    |
| ShowMaskOnFocus      | Shows the mask when the input gets focus. (default = true)                                                                                                                                                                                                            | bool                     | true                                     |
| ShowMaskOnHover      | Shows the mask when hovering the mouse. (default = true)                                                                                                                                                                                                              | bool                     | true                                     |
| Size                 | Sets the size of the input control.                                                                                                                                                                                                                                   | Size?                    | null                                     |
| TabIndex             | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                                                         | int?                     | null                                     |
| Value                | Gets or sets the input time value.                                                                                                                                                                                                                                    | string                   |                                          |
| ValueExpression      | Gets or sets an expression that identifies the time field.                                                                                                                                                                                                            | Expression<Func<string>> | null                                     |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| Cleared               | Execute a function when the mask is cleared.                                                                                                                                                                                                                                           | EventCallback                    |
| Completed             | Execute a function when the mask is completed.                                                                                                                                                                                                                                         | EventCallback<string>            |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| Incompleted           | Execute a function when the mask is incomplete. Executes on blur.                                                                                                                                                                                                                      | EventCallback<string>            |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |
| ValueChanged          | Occurs when the time has changed.                                                                                                                                                                                                                                                      | EventCallback<string>            |

### Methods

| Method            | Description                                                                                  | Return   | Parameters           |
|-------------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| ExtendAliases     | Extends the alias options with the custom settings.                                          | Task     | object aliasOptions  |
| NotifyCompleted   | Notifies the component that the input mask is completed.                                     | Task     | string value         |
| NotifyIncompleted | Notifies the component that the input mask is incomplete.                                    | Task     | string value         |
| NotifyCleared     | Notifies the component that the input mask is cleared.                                       | Task     |                      |
| Select            | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus             | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate        | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 