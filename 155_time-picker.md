# Blazorise TimePicker component

A customizable time input component with an option to manually write time or choose from a menu.

The &lt;TimePicker&gt; is stand-alone component that can be utilized in many existing Blazorise components. It offers the user a visual representation for selecting the time.

TimePicker is based on a flatpickr time picker
    and as such is not a native time input element. That means that unlike TimeEdit which will render type="time",
    TimePicker will render type="text" in the DOM.

## Examples

### Basic example

In the following example, the Blazorise TimePicker is easily set up and bound to a value by setting the  directive.

```
<TimePicker TValue="TimeSpan?" @bind-Time="@value" />
```

```
@code {
    TimeSpan? value;
}
```

### DateTime example

In the following example, the Blazorise TimePicker component is easily configured to bind with a  type, demonstrating its versatility.

```
<TimePicker TValue="DateTime?" @bind-Time="@value" />
```

```
@code {
    DateTime? value;
}
```

### Add icon

To add icon you can combine  with an .

```
<Addons>
    <Addon AddonType="AddonType.Body">
        <TimePicker @ref="@timePicker" TValue="TimeSpan?" @bind-Time="@value" />
    </Addon>
    <Addon AddonType="AddonType.End">
        <Button Color="Color.Light" Clicked="@(()=>timePicker.ToggleAsync())">
            <Icon Name="IconName.CalendarDay" />
        </Button>
    </Addon>
</Addons>
```

```
@code{
    TimePicker<TimeSpan?> timePicker;

    TimeSpan? value;
}
```

### Inline Time

To always show the time menu you just need to set  parameter.

```
<TimePicker TValue="TimeSpan?" @bind-Time="@value" Inline />
```

```
@code {
    TimeSpan? value;
}
```

### Non Static example

By default, the time menu will position statically. This means that it will also keep its position relative to the page when you scroll.

If you want to disable this behavior, you should assign the value false to the StaticPicker parameter.

```
<TimePicker TValue="TimeSpan?" @bind-Time="@value" StaticPicker="false" />
```

```
@code {
    TimeSpan? value;
}
```

## API

### Parameters

| Parameter        | Description                                                                                                                                          | Type                     | Default       |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|---------------|
| Autofocus        | Set's the focus to the component after the rendering is done.                                                                                        | bool                     | false         |
| ChildContent     | Specifies the content to be rendered inside this TimePicker.                                                                                         | RenderFragment           | null          |
| Color            | Sets the input text color.                                                                                                                           | Color                    | Color.Default |
| Debounce         | If true the entered text will be slightly delayed before submitting it to the internal value.                                                        | bool?                    | null          |
| DebounceInterval | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                    | int?                     | null          |
| Disabled         | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                              | bool                     | false         |
| DisplayFormat    | Defines the display format of the time input.                                                                                                        | string                   |               |
| Feedback         | Placeholder for validation messages.                                                                                                                 | RenderFragment           | null          |
| Immediate        | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate. | bool?                    | null          |
| Inline           | Display the time menu in an always-open state with the inline option.                                                                                | bool                     | false         |
| Max              | The latest time to accept.                                                                                                                           | TimeSpan?                | null          |
| Min              | The earliest time to accept.                                                                                                                         | TimeSpan?                | null          |
| Pattern          | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                           | string                   |               |
| Placeholder      | Sets the placeholder for the empty text.                                                                                                             | string                   |               |
| Plaintext        | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                 | bool                     | false         |
| ReadOnly         | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                         | bool                     | false         |
| Size             | Sets the size of the input control.                                                                                                                  | Size?                    | null          |
| StaticPicker     | If enabled, the calendar menu will be positioned as static.                                                                                          | bool                     | true          |
| TabIndex         | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                        | int?                     | null          |
| Time             | Gets or sets the input time value.                                                                                                                   | TValue                   | null          |
| TimeAs24hr       | Displays time picker in 24 hour mode without AM/PM selection when enabled.                                                                           | bool                     | false         |
| TimeExpression   | Gets or sets an expression that identifies the time field.                                                                                           | Expression<Func<TValue>> | null          |

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

| Method      | Description                                                                                  | Return    | Parameters           |
|-------------|----------------------------------------------------------------------------------------------|-----------|----------------------|
| OpenAsync   | Opens the time dropdown.                                                                     | ValueTask |                      |
| CloseAsync  | Closes the time dropdown.                                                                    | ValueTask |                      |
| ToggleAsync | Shows/opens the time dropdown if its closed, hides/closes it otherwise.                      | ValueTask |                      |
| Select      | Select all text in the underline component.                                                  | Task      | bool focus           |
| Focus       | Sets the focus on the underline element.                                                     | Task      | bool scrollToElement |
| Revalidate  | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task      |                      |

###### On this page

#### 

## 