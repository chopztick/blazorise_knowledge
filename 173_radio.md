# Blazorise Radio component

The Radio allow the user to select a single option from a group.

Radio Button Group allows the user to select exactly one value from a list of related, but mutually exclusive, options.

## Structure

- &lt; RadioGroup&gt; main component for grouping radios.
- &lt;RadioGroup&gt; main component for grouping radios.
    - &lt;Radio&gt; radio button, which can be grouped or standalone.

## Examples

### Basic RadioGroup

is a helpful wrapper used to group  components that provides an easier API,
        and proper keyboard accessibility to the group.

```
<RadioGroup TValue="string" Name="colors">
    <Radio Value="@("red")">Red</Radio>
    <Radio Value="@("green")">Green</Radio>
    <Radio Value="@("blue")">Blue</Radio>
</RadioGroup>
```

Important Note:
        
        
            For the RadioGroup and Radio components to work correctly, the TValue type must match across both. This is especially important when using nullable types, as mismatched types can lead to unexpected behavior.

### Standalone Radio

can also be used standalone, without the  wrapper.

```
<Radio TValue="string" Group="colors" Value="@("red")">Red</Radio>
<Radio TValue="string" Group="colors" Value="@("green")">Green</Radio>
<Radio TValue="string" Group="colors" Value="@("blue")">Blue</Radio>
```

### RadioGroup Buttons

By setting the  flag, radios will be grouped together and will appear as buttons.

```
<RadioGroup TValue="string" Name="colors" Buttons>
    <Radio Value="@("red")">Red</Radio>
    <Radio Value="@("green")">Green</Radio>
    <Radio Value="@("blue")">Blue</Radio>
</RadioGroup>
```

### Custom Button Colors

Changing the color of the radio buttons is as simple as setting the  attribute on a  component.

```
<RadioGroup TValue="string" Name="side" Buttons>
    <Radio Value="@("left")" Color="Color.Danger">Left</Radio>
    <Radio Value="@("middle")" Color="Color.Warning">Middle</Radio>
    <Radio Value="@("right")" Color="Color.Success">Right</Radio>
</RadioGroup>
```

## Binding

### Two-way binding

```
<RadioGroup TValue="string" Name="colors" @bind-CheckedValue="@checkedValue">
    <Radio Value="@("red")">Red</Radio>
    <Radio Value="@("green")">Green</Radio>
    <Radio Value="@("blue")">Blue</Radio>
</RadioGroup>
```

```
@code{
    string checkedValue = "green";
}
```

### Manual event binding

```
<RadioGroup TValue="string"
            Name="colors"
            CheckedValue="@checkedValue"
            CheckedValueChanged="@OnCheckedValueChanged">
    <Radio Value="@("red")">Red</Radio>
    <Radio Value="@("green")">Green</Radio>
    <Radio Value="@("blue")">Blue</Radio>
</RadioGroup>
```

```
@code{
    string checkedValue = "green";

    Task OnCheckedValueChanged( string value )
    {
        checkedValue = value;

        return Task.CompletedTask;
    }
}
```

## API

### Parameters

#### RadioGroup

| Parameter              | Description                                                                                                   | Type                     | Default                |
|------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------|------------------------|
| Autofocus              | Set's the focus to the component after the rendering is done.                                                 | bool                     | false                  |
| Buttons                | Flag which indicates that radios will appear as button.                                                       | bool                     | false                  |
| CheckedValue           | Gets or sets the checked value.                                                                               | TValue                   | null                   |
| CheckedValueExpression | Gets or sets an expression that identifies the checked value.                                                 | Expression<Func<TValue>> | null                   |
| ChildContent           | Specifies the content to be rendered inside this RadioGroup.                                                  | RenderFragment           | null                   |
| Color                  | Defines the color or radio buttons(only when RadioGroup.Buttons is true).                                     | Color                    | Color.Secondary        |
| Disabled               | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                     | false                  |
| Feedback               | Placeholder for validation messages.                                                                          | RenderFragment           | null                   |
| Name                   | Radio group name.                                                                                             | string                   |                        |
| Orientation            | Defines the orientation of the radio elements.Possible values:Horizontal, Vertical                            | Orientation              | Orientation.Horizontal |
| ReadOnly               | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                     | false                  |
| Size                   | Sets the size of the input control.                                                                           | Size?                    | null                   |
| TabIndex               | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                     | null                   |

#### Radio

| Parameter         | Description                                                                                                   | Type                     | Default        |
|-------------------|---------------------------------------------------------------------------------------------------------------|--------------------------|----------------|
| Autofocus         | Set's the focus to the component after the rendering is done.                                                 | bool                     | false          |
| Checked           | Gets or sets the checked flag.                                                                                | TValue                   | null           |
| CheckedExpression | Gets or sets an expression that identifies the checked value.                                                 | Expression<Func<TValue>> | null           |
| ChildContent      | Specifies the content to be rendered inside this Radio.                                                       | RenderFragment           | null           |
| Color             | Defines the color of a radio button(only when RadioGroup.Buttons is true).                                    | Color                    | null           |
| Cursor            | Defines the mouse cursor based on the behaviour by the current css framework.Possible values:Default, Pointer | Cursor                   | Cursor.Default |
| Disabled          | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                     | false          |
| Feedback          | Placeholder for validation messages.                                                                          | RenderFragment           | null           |
| Group             | Sets the radio group name.                                                                                    | string                   |                |
| Inline            | Group checkboxes or radios on the same horizontal row.                                                        | bool                     | false          |
| ReadOnly          | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                     | false          |
| Size              | Sets the size of the input control.                                                                           | Size?                    | null           |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                     | null           |
| Value             | Gets or sets the radio value.                                                                                 | TValue                   | null           |

### Events

#### RadioGroup

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| CheckedValueChanged   | Occurs when the checked value is changed.                                                                                                                                                                                                                                              | EventCallback<TValue>            |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |

#### Radio

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

#### RadioGroup

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

#### Radio

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 