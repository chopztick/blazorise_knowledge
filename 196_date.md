# Blazorise DateEdit component

DateEdit is an input field that allows the user to enter a date by typing or by selecting from a calendar overlay.

A native date &lt;input&gt; component built around the &lt;input type="date"&gt;.

Being built around native &lt;input type="date"&gt; input element, the DateEdit component
    comes with a few limitations that you must be aware of. First and foremost, the input display format is fully
    controlled by the browser and the system locale. This means that for you to change the input format you would
    need to change the browser settings.

### Basic example

```
<DateEdit TValue="DateTime?" />
```

## Binding

### Two-way binding

By using  attribute the selected date will be automatically assigned to the member variable.

```
<DateEdit TValue="DateTime?" @bind-Date="@selectedDate" />
```

```
@code{
    DateTime? selectedDate;
}
```

### Manual event binding

When using the event , you also must define the  value attribute.

```
<DateEdit TValue="DateTime?" Date="@selectedDate" DateChanged="@OnDateChanged" />
```

```
@code{
    DateTime? selectedDate;

    void OnDateChanged( DateTime? date )
    {
        selectedDate = date;
    }
}
```

### DateTime

DateEdit component also support entering a time part. To enable it just set  parameter.

```
<DateEdit TValue="DateTime?" InputMode="DateInputMode.DateTime" />
```

### Show Picker

If you want to show the default picker that comes with the date input element you can make it by using the ShowPicker() function.

Note: Keep in mind that not all browser will support the ShowPicker() function.

```
<Field>
    <Button Color="Color.Primary" Clicked="@(()=>dateEditRef.ShowPicker())">
        Show Picker
    </Button>
</Field>
<Field>
    <DateEdit @ref="@dateEditRef" TValue="DateTime" />
</Field>
```

```
@code {
    DateEdit<DateTime> dateEditRef;
}
```

## API

### Parameters

| Parameter        | Description                                                                                                                                                                                                       | Type                     | Default            |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------|
| Autofocus        | Set's the focus to the component after the rendering is done.                                                                                                                                                     | bool                     | false              |
| ChildContent     | Specifies the content to be rendered inside this DateEdit.                                                                                                                                                        | RenderFragment           | null               |
| Color            | Sets the input text color.                                                                                                                                                                                        | Color                    | Color.Default      |
| Date             | Gets or sets the input date value.                                                                                                                                                                                | TValue                   | null               |
| DateExpression   | Gets or sets an expression that identifies the date value.                                                                                                                                                        | Expression<Func<TValue>> | null               |
| Debounce         | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                     | bool?                    | null               |
| DebounceInterval | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                 | int?                     | null               |
| Disabled         | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                           | bool                     | false              |
| Feedback         | Placeholder for validation messages.                                                                                                                                                                              | RenderFragment           | null               |
| Immediate        | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                              | bool?                    | null               |
| InputMode        | Hints at the type of data that might be entered by the user while editing the element or its contents.Possible values:Date, DateTime, Month                                                                       | DateInputMode            | DateInputMode.Date |
| Max              | The latest date to accept.                                                                                                                                                                                        | DateTimeOffset?          | null               |
| Min              | The earliest date to accept.                                                                                                                                                                                      | DateTimeOffset?          | null               |
| Pattern          | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                                                                                        | string                   |                    |
| Placeholder      | Sets the placeholder for the empty text.                                                                                                                                                                          | string                   |                    |
| Plaintext        | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                                                              | bool                     | false              |
| ReadOnly         | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                      | bool                     | false              |
| Size             | Sets the size of the input control.                                                                                                                                                                               | Size?                    | null               |
| Step             | The step attribute specifies the legal day intervals to choose from when the user opens the calendar in a date field.           For example, if step = "2", you can only select every second day in the calendar. | int                      | 1                  |
| TabIndex         | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                     | int?                     | null               |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| DateChanged           | Occurs when the date has changed.                                                                                                                                                                                                                                                      | EventCallback<TValue>            |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| ShowPicker | Show a browser picker for the date input.                                                    | Task     |                      |
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 