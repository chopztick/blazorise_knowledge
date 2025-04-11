# Blazorise TimeEdit component

A native time input component build around the &lt;input type="time"&gt;.

## Examples

### Basic

A native time field example with .

```
<TimeEdit TValue="TimeSpan?" />
```

## Binding

### Two-way binding

By using  attribute the selected time will be automatically assigned to the member variable.

```
<TimeEdit TValue="TimeSpan?" @bind-Time="@selectedTime" />
```

```
@code{
    TimeSpan? selectedTime;
}
```

### Manual event binding

When using the event , you also must define the  value attribute.

```
<TimeEdit TValue="TimeSpan?" Time="@selectedTime" TimeChanged="@OnTimeChanged" />
```

```
@code{
    TimeSpan? selectedTime;

    Task OnTimeChanged( TimeSpan? Time )
    {
        selectedTime = Time;

        return Task.CompletedTask;
    }
}
```

### Show Picker

If you want to show the default picker that comes with the time input element you can make it by using the ShowPicker() function.

Note: Keep in mind that not all browser will support the ShowPicker() function.

```
<Field>
    <Button Color="Color.Primary" Clicked="@(()=>timeEditRef.ShowPicker())">
        Show Picker
    </Button>
</Field>
<Field>
    <TimeEdit @ref="@timeEditRef" TValue="DateTime" />
</Field>
```

```
@code {
    TimeEdit<DateTime> timeEditRef;
}
```

## Functions

| Name         | Description                               |
|--------------|-------------------------------------------|
| ShowPicker() | Show a browser picker for the time input. |

## API

### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                        | Type                     | Default       |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|---------------|
| Autofocus        | Set's the focus to the component after the rendering is done.                                                                                                                                                                                                                                                                      | bool                     | false         |
| ChildContent     | Specifies the content to be rendered inside this TimeEdit.                                                                                                                                                                                                                                                                         | RenderFragment           | null          |
| Color            | Sets the input text color.                                                                                                                                                                                                                                                                                                         | Color                    | Color.Default |
| Debounce         | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                                                                                                                                      | bool?                    | null          |
| DebounceInterval | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                                                                                                                                  | int?                     | null          |
| Disabled         | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                                                                                                                            | bool                     | false         |
| Feedback         | Placeholder for validation messages.                                                                                                                                                                                                                                                                                               | RenderFragment           | null          |
| Immediate        | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                                                                                                                                               | bool?                    | null          |
| Max              | The latest time to accept.                                                                                                                                                                                                                                                                                                         | TimeSpan?                | null          |
| Min              | The earliest time to accept.                                                                                                                                                                                                                                                                                                       | TimeSpan?                | null          |
| Pattern          | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                                                                                                                                                                                                         | string                   |               |
| Placeholder      | Sets the placeholder for the empty text.                                                                                                                                                                                                                                                                                           | string                   |               |
| Plaintext        | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                                                                                                                                                                               | bool                     | false         |
| ReadOnly         | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                                                                                                                                       | bool                     | false         |
| Size             | Sets the size of the input control.                                                                                                                                                                                                                                                                                                | Size?                    | null          |
| Step             | The step attribute specifies the legal number intervals for seconds or milliseconds in a time field (does not apply for hours or minutes).          Example: if step="2", legal numbers could be 0, 2, 4, etc.Remarks The step attribute is often used together with the max and min attributes to create a range of legal values. | int?                     | null          |
| TabIndex         | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                                                                                                                      | int?                     | null          |
| Time             | Gets or sets the input time value.                                                                                                                                                                                                                                                                                                 | TValue                   | null          |
| TimeExpression   | Gets or sets an expression that identifies the time field.                                                                                                                                                                                                                                                                         | Expression<Func<TValue>> | null          |

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
| TimeChanged           | Occurs when the time has changed.                                                                                                                                                                                                                                                      | EventCallback<TValue>            |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| ShowPicker | Show a browser picker for the time input.                                                    | Task     |                      |
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 