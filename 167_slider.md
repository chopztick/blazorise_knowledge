# Blazorise Slider component

Sliders allow users to make selections from a range of values.

Sliders reflect a range of values along a bar, from which users may select a single value. They are ideal for adjusting settings such as volume, brightness, or applying image filters.

## Examples

### Basic

```
<Slider TValue="decimal" Value="25m" Max="100m" />
```

Since Slider is a generic component you will have to specify the exact data type for the value.
        Most of the time it will be recognized automatically when you set the  attribute, but if not
        you will just use the  attribute and define the type manually.

### Min and Max values

With the  and  properties, you can set the minimum and maximum allowed value.

Current value: 60

```
<Paragraph>
    Current value: @value
</Paragraph>

<Field>
    <Slider @bind-Value="@value" Min="20" Max="80" />
</Field>
```

```
@code {
    int value = 60;
}
```

### Steps

You can change the default step increment.

Current value: 40

```
<Paragraph>
    Current value: @value
</Paragraph>

<Field>
    <Slider @bind-Value="@value" Step="5" Max="100" />
</Field>
```

```
@code {
    int value = 40;
}
```

## API

### Parameters

| Parameter       | Description                                                                                                   | Type                     | Default   |
|-----------------|---------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| Autofocus       | Set's the focus to the component after the rendering is done.                                                 | bool                     | false     |
| ChildContent    | Specifies the content to be rendered inside this Slider.                                                      | RenderFragment           | null      |
| Disabled        | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                     | false     |
| Feedback        | Placeholder for validation messages.                                                                          | RenderFragment           | null      |
| Max             | The maximum value to accept for this input.                                                                   | TValue                   | null      |
| Min             | The minimum value to accept for this input.                                                                   | TValue                   | null      |
| ReadOnly        | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                     | false     |
| Size            | Sets the size of the input control.                                                                           | Size?                    | null      |
| Step            | Specifies the interval between valid values.                                                                  | TValue                   | null      |
| TabIndex        | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                     | null      |
| Value           | Gets or sets the value inside the input field.                                                                | TValue                   | null      |
| ValueExpression | Gets or sets an expression that identifies the checked value.                                                 | Expression<Func<TValue>> | null      |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |
| ValueChanged          | Occurs after the value has changed.Remarks This will be converted to EventCallback once the Blazor team fix the error for generic components. see https://github.com/aspnet/AspNetCore/issues/8385                                                                                     | EventCallback<TValue>            |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 