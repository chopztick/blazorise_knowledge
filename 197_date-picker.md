# Blazorise DatePicker component

DatePicker is an input field that allows the user to enter a date by typing or by selecting from a calendar overlay.

&lt;DatePicker&gt; is a fully featured date selection component that lets users select a date.
    DatePicker is based on a flatpickr datetime picker
    and as such is not a native date input element. That means that unlike DateEdit which will render type="date",
    DatePicker will render type="text" in the DOM.

## Examples

### Basic example

```
<DatePicker TValue="DateTime?" @bind-Date="@value" />
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
        <DatePicker @ref="@datePicker" TValue="DateTime?" @bind-Date="@value" />
    </Addon>
    <Addon AddonType="AddonType.End">
        <Button Color="Color.Light" Clicked="@(()=>datePicker.ToggleAsync())">
            <Icon Name="IconName.CalendarDay" />
        </Button>
    </Addon>
</Addons>
```

```
@code {
    DatePicker<DateTime?> datePicker;

    DateTime? value;
}
```

### Disable dates

If you’d like to make certain dates unavailable for selection you can assign the  parameter.

```
<DatePicker TValue="DateTime?" DisabledDates="@disabledDates" />
```

```
@code {
    DateTime?[] disabledDates = new DateTime?[] {
        DateTime.Now.AddDays(-1),
        DateTime.Now.AddDays(2),
    };
}
```

### Enable dates

If you’d like to make only certain dates available for selection, you can assign the  parameter.

```
<DatePicker TValue="DateTime?" EnabledDates="@enabledDates" />
```

```
@code {
    DateTime?[] enabledDates = new DateTime?[]{
        DateTime.Now.AddDays(-1),
        DateTime.Now.AddDays(2),
    };
}
```

### Disable days

If you’d like to make only certain days in a week unavailable for selection you can assign the  parameter.

```
<DatePicker TValue="DateTime?" DisabledDays="@disabledDays" />
```

```
@code {
    DayOfWeek[] disabledDays = new[]  {
        DayOfWeek.Saturday,
        DayOfWeek.Sunday,
    };
}
```

### Range example

Select a range of dates using the range calendar.

```
<DatePicker TValue="DateTime?" @bind-Dates="selectedDates" InputMode="DateInputMode.Date" SelectionMode="DateInputSelectionMode.Range" />
```

```
@code {
    IReadOnlyList<DateTime?> selectedDates;
}
```

### Multiple example

It is possible to select multiple dates.

```
<DatePicker @bind-Dates="selectedDates" TValue="DateTime?" InputMode="DateInputMode.Date" SelectionMode="DateInputSelectionMode.Multiple" />
```

```
@code{
    IReadOnlyList<DateTime?> selectedDates;
}
```

### Inline Calendar

To always show the calendar you just need to set  parameter.

```
<DatePicker TValue="DateTime?" @bind-Date="@value" Inline />
```

```
@code {
    DateTime? value;
}
```

### Non Static example

By default, the calendar menu will position statically. This means that it will also keep its position relative to the page when you scroll.

If you want to disable this behavior, you should assign the value false to the StaticPicker parameter.

```
<DatePicker TValue="DateTime?" @bind-Date="@value" StaticPicker="false" />
```

```
@code {
    DateTime? value;
}
```

### Input format mask

In this example, the user is prompted to enter a value in the format dd.MM.yyyy.

Notice that we have also defined a DisplayFormat parameter. This is needed so that after the user finish with the input mask we need to properly parse it using the same format.

```
<DatePicker TValue="DateTime?" @bind-Date="@value" InputFormat="dd.MM.yyyy" DisplayFormat="dd.MM.yyyy" />
```

```
@code {
    DateTime? value;
}
```

## Formats

### Display Format

Native Flatpickr component has some special rules regarding the date format string. To make it easier to use we
    tried to map the flatpickr custom formatter to behave as close to .NET date format string.

Bellow you can find the list of available and supported mappings between Blazorise and flatpickr.

| .NET value   | Flatpickr value   | Description                                                                    |
|--------------|-------------------|--------------------------------------------------------------------------------|
| d            | j                 | Day of the month without leading zeros, 1 to 31.                               |
| dd           | d                 | Day of the month, 2 digits with leading zeros, 01 to 31.                       |
| ddd          | D                 | A textual representation of a day, Mon through Sun.                            |
| dddd         | l                 | A full textual representation of the day of the week, Sunday through Saturday. |
| M            | n                 | Numeric representation of a month, without leading zeros, 1 through 12.        |
| MM           | m                 | Numeric representation of a month, with leading zero, 01 through 12.           |
| MMM          | M                 | A short textual representation of a month, Jan through Dec.                    |
| MMMM         | F                 | A full textual representation of a month, January through December.            |
| y            | y                 | A two digit representation of a year. 99 or 03.                                |
| yy           | y                 | -||-                                                                           |
| yyy          | Y                 | A full numeric representation of a year, 4 digits, 1999 or 2003.               |
| yyyy         | Y                 | -||-                                                                           |
| yyyy         | Y                 | -||-                                                                           |
| H            | H                 | Hours (24 hours), 00 to 23.                                                    |
| HH           | H                 | -||-                                                                           |
| h            | h                 | Hours, 1 to 12.                                                                |
| hh           | G                 | Hours, 2 digits with leading zeros, 01 to 12.                                  |
| m            | i                 | Minutes, 00 to 59.                                                             |
| mm           | i                 | -||-                                                                           |
| s            | s                 | Seconds, 0, 1 to 59.                                                           |
| ss           | S                 | Seconds, 2 digits, 00 to 59.                                                   |
| t            | K                 | AM/PM designator.                                                              |
| tt           | K                 | -||-                                                                           |

### Input Format

We use the Inputmask library for handling of the datetime edit masks.

Bellow you can find the list of available and supported mappings between Blazorise and Inputmask.

| .NET value   | Inputmask value   | Description                                                                                                            |
|--------------|-------------------|------------------------------------------------------------------------------------------------------------------------|
| d            | d                 | Day of the month as digits; no leading zero for single-digit days.                                                     |
| dd           | dd                | Day of the month as digits; leading zero for single-digit days.                                                        |
| ddd          | ddd               | Day of the week as a three-letter abbreviation.                                                                        |
| dddd         | dddd              | Day of the week as its full name.                                                                                      |
| M            | m                 | Month as digits; no leading zero for single-digit months.                                                              |
| MM           | mm                | Month as digits; leading zero for single-digit months.                                                                 |
| MMM          | mmm               | Month as a three-letter abbreviation.                                                                                  |
| MMMM         | mmmm              | Month as its full name.                                                                                                |
| yy           | yy                | Year as last two digits; leading zero for years less than 10.                                                          |
| yyyy         | yyyy              | Year as 4 digits.                                                                                                      |
| h            | h                 | Hours; no leading zero for single-digit hours (12-hour clock).                                                         |
| hh           | hh                | Hours; leading zero for single-digit hours (12-hour clock).                                                            |
| HH           | HH                | Hours; leading zero for single-digit hours (24-hour clock).                                                            |
| m            | M                 | Minutes; no leading zero for single-digit minutes. Uppercase M unlike CF timeFormat's m to avoid conflict with months. |
| mm           | MM                | Minutes; leading zero for single-digit minutes. Uppercase MM unlike CF timeFormat's mm to avoid conflict with months.  |
| s            | s                 | Seconds; no leading zero for single-digit seconds.                                                                     |
| ss           | ss                | Seconds; leading zero for single-digit seconds.                                                                        |
| t            | T                 | Single-character time marker string: A or P.                                                                           |
| tt           | TT                | Two-character time marker string: AM or PM.                                                                            |

## Best Practices

### Show the Date Format

Use a placeholder or helper to show how the input should be formatted. For example, "12/6/2020" represents different dates for Americans and Europeans.

Helpers are preferable to placeholders, as they are always visible. Fields with placeholders are also less noticeable than empty fields, so they are susceptible to being skipped. Use placeholders when space is limited, for example when Date Picker is used as a filter in a data grid header.

```
<Field>
    <FieldLabel>Start date</FieldLabel>
    <FieldBody>
        <DatePicker TValue="DateTime?" Placeholder="DD/MM/YYYY" />
    </FieldBody>
    <FieldHelp>Format: DD/MM/YYYY</FieldHelp>
</Field>
```

## API

### Parameters

| Parameter        | Description                                                                                                                                          | Type                                    | Default                       |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|-------------------------------|
| Autofocus        | Set's the focus to the component after the rendering is done.                                                                                        | bool                                    | false                         |
| ChildContent     | Specifies the content to be rendered inside this DatePicker.                                                                                         | RenderFragment                          | null                          |
| Color            | Sets the input text color.                                                                                                                           | Color                                   | Color.Default                 |
| Date             | Gets or sets the input date value.                                                                                                                   | TValue                                  | null                          |
| DateExpression   | Gets or sets an expression that identifies the date value.                                                                                           | Expression<Func<TValue>>                | null                          |
| Dates            | Gets or sets the input date value.                                                                                                                   | IReadOnlyList<TValue>                   | null                          |
| DatesExpression  | Gets or sets an expression that identifies the date value.                                                                                           | Expression<Func<IReadOnlyList<TValue>>> | null                          |
| Debounce         | If true the entered text will be slightly delayed before submitting it to the internal value.                                                        | bool?                                   | null                          |
| DebounceInterval | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                    | int?                                    | null                          |
| Disabled         | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                              | bool                                    | false                         |
| DisabledDates    | List of disabled dates that the user should not be able to pick.                                                                                     | IEnumerable<TValue>                     | null                          |
| DisabledDays     | List of disabled days in a week that the user should not be able to pick.                                                                            | IEnumerable<DayOfWeek>                  | null                          |
| DisableMobile    | If enabled, it disables the native input on mobile devices.                                                                                          | bool                                    | true                          |
| DisplayFormat    | Defines the display format of the date input.                                                                                                        | string                                  |                               |
| EnabledDates     | List of enabled dates that the user should be able to pick.                                                                                          | IEnumerable<TValue>                     | null                          |
| Feedback         | Placeholder for validation messages.                                                                                                                 | RenderFragment                          | null                          |
| FirstDayOfWeek   | Defines the first day of the week.                                                                                                                   | DayOfWeek                               | DayOfWeek.Monday              |
| Immediate        | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate. | bool?                                   | null                          |
| Inline           | Display the calendar in an always-open state with the inline option.                                                                                 | bool                                    | false                         |
| InputFormat      | Defines the input format mask of the date input.                                                                                                     | string                                  |                               |
| InputMode        | Hints at the type of data that might be entered by the user while editing the element or its contents.Possible values:Date, DateTime, Month          | DateInputMode                           | DateInputMode.Date            |
| Max              | The latest date to accept.                                                                                                                           | DateTimeOffset?                         | null                          |
| Min              | The earliest date to accept.                                                                                                                         | DateTimeOffset?                         | null                          |
| Pattern          | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                           | string                                  |                               |
| Placeholder      | Sets the placeholder for the empty text.                                                                                                             | string                                  |                               |
| Plaintext        | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                 | bool                                    | false                         |
| RangeSeparator   | Overrides the range separator that is used to separate date values when DatePicker.SelectionMode is set to DateInputSelectionMode.Range.             | string                                  |                               |
| ReadOnly         | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                         | bool                                    | false                         |
| SelectionMode    | Defines the mode in which the dates can be selected.Possible values:Single, Range, Multiple                                                          | DateInputSelectionMode                  | DateInputSelectionMode.Single |
| Size             | Sets the size of the input control.                                                                                                                  | Size?                                   | null                          |
| StaticPicker     | If enabled, the calendar menu will be positioned as static.                                                                                          | bool                                    | true                          |
| TabIndex         | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                        | int?                                    | null                          |
| TimeAs24hr       | Displays time picker in 24 hour mode without AM/PM selection when enabled.                                                                           | bool                                    | false                         |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                                 |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>        |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                         |
| DateChanged           | Occurs when the date has changed.                                                                                                                                                                                                                                                      | EventCallback<TValue>                |
| DatesChanged          | Occurs when the date has changed.                                                                                                                                                                                                                                                      | EventCallback<IReadOnlyList<TValue>> |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>        |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>        |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs>     |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs>     |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs>     |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>        |

### Methods

| Method            | Description                                                                                  | Return    | Parameters                  |
|-------------------|----------------------------------------------------------------------------------------------|-----------|-----------------------------|
| OnKeyDownHandler  | Handler for @onkeydown event.                                                                | Task      | KeyboardEventArgs eventArgs |
| OnKeyUpHandler    | Handler for @onkeyup event.                                                                  | Task      | KeyboardEventArgs eventArgs |
| OnFocusHandler    | Handler for @onfocus event.                                                                  | Task      | FocusEventArgs eventArgs    |
| OnFocusInHandler  | Handler for @onfocusin event.                                                                | Task      | FocusEventArgs eventArgs    |
| OnFocusOutHandler | Handler for @onfocusout event.                                                               | Task      | FocusEventArgs eventArgs    |
| OnKeyPressHandler | Handler for @onkeypress event.                                                               | Task      | KeyboardEventArgs eventArgs |
| OnBlurHandler     | Handler for @onblur event.                                                                   | Task      | FocusEventArgs eventArgs    |
| OpenAsync         | Opens the calendar dropdown.                                                                 | ValueTask |                             |
| CloseAsync        | Closes the calendar dropdown.                                                                | ValueTask |                             |
| ToggleAsync       | Shows/opens the calendar if its closed, hides/closes it otherwise.                           | ValueTask |                             |
| Select            | Select all text in the underline component.                                                  | Task      | bool focus                  |
| Focus             | Sets the focus on the underline element.                                                     | Task      | bool scrollToElement        |
| Revalidate        | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task      |                             |

###### On this page

#### 

## 