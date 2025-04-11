# Blazorise NumericPicker component

A customizable NumericPicker component allows you to enter numeric values and contains controls for increasing and reducing the value.

Use &lt;NumericPicker&gt; to have a field for any kind of numeric values.

All basic types are supported, including nullable types: (int, long, float, double, decimal, etc.).

## Examples

### Basic

```
<NumericPicker Value="123" />
```

## Rules

### Generic type

Since  is a generic component you will have to specify the exact data type for the value.
        Most of the time it will be recognized automatically when you set the  attribute, but if
        not you will just use the  attribute and define the type manually eg.

```
<NumericPicker TValue="decimal?" />
```

### Curency symbols

The display format of the  can be adjusted to provide more context for the value it represents,
        such as displaying currency. By defining the  parameter you can use any symbol. Additionally you can define the symbol position
        with the  parameter.

```
<NumericPicker TValue="decimal?" CurrencySymbol="$" Value="456" />
```

### Controlling the step value

Set the amount to increment or decrement the value when the spinner buttons are used with the  parameter.

```
<NumericPicker @bind-Value="@value" Step="10" />
```

```
@code{
    decimal value;
}
```

### Setting the Min &amp; Max

Set the  &amp;  to limit the values allowed into the input.

```
<NumericPicker @bind-Value="@value" Min="10" Max="20" />
```

```
@code{
    decimal value = 15;
}
```

### Integer values

If you define a  as an integer type,  will automatically ignore  parameter and you will only be able to enter number without decimals.

```
<NumericPicker @bind-Value="@value" />
```

```
@code{
    int value;
}
```

### Modify Value With Mouse Wheel

Sometime you want to be able to change the value by scrolling with the mouse wheel when it is focused over the input. To enable it just use the  parameter.

```
<NumericPicker @bind-Value="@value" ModifyValueOnWheel WheelOn="NumericWheelOn.Hover" />
```

```
@code {
    decimal value;
}
```

## API

### Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                                                                                | Type                        | Default                               |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|---------------------------------------|
| AllowDecimalPadding         | Allow padding the decimal places with zeros. If set to Floats, padding is only done when there are some decimals.Possible values:Always, Never, FloatsRemarks Setting AllowDecimalPadding to 'false' will override the NumericPicker.Decimals setting.                                                                     | NumericAllowDecimalPadding  | NumericAllowDecimalPadding.Always     |
| AlternativeDecimalSeparator | String to use as the alternative decimal separator in numeric values.                                                                                                                                                                                                                                                      | string                      | ","                                   |
| AlwaysAllowDecimalSeparator | Defines if the decimal character or decimal character alternative should be accepted when there is already a decimal character shown in the element.                                                                                                                                                                       | bool                        | false                                 |
| Autofocus                   | Set's the focus to the component after the rendering is done.                                                                                                                                                                                                                                                              | bool                        | false                                 |
| ChildContent                | Specifies the content to be rendered inside this NumericPicker.                                                                                                                                                                                                                                                            | RenderFragment              | null                                  |
| Color                       | Sets the input text color.                                                                                                                                                                                                                                                                                                 | Color                       | Color.Default                         |
| Culture                     | Helps define the language of an element. See w3schools.com.                                                                                                                                                                                                                                                                | string                      |                                       |
| CurrencySymbol              | Defines the currency symbol to display.                                                                                                                                                                                                                                                                                    | string                      |                                       |
| CurrencySymbolPlacement     | Placement of the currency sign, relative to the number shown (as a prefix or a suffix).Possible values:Prefix, Suffix                                                                                                                                                                                                      | CurrencySymbolPlacement     | CurrencySymbolPlacement.Prefix        |
| Debounce                    | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                                                                                                                              | bool?                       | null                                  |
| DebounceInterval            | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                                                                                                                          | int?                        | null                                  |
| Decimals                    | Maximum number of decimal places after the decimal separator.                                                                                                                                                                                                                                                              | int                         | 2                                     |
| DecimalSeparator            | String to use as the decimal separator in numeric values.                                                                                                                                                                                                                                                                  | string                      | "."                                   |
| Disabled                    | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                                                                                                                    | bool                        | false                                 |
| EnableStep                  | If true, enables change of numeric value by pressing on step buttons or by keyboard up/down keys.                                                                                                                                                                                                                          | bool?                       | null                                  |
| Feedback                    | Placeholder for validation messages.                                                                                                                                                                                                                                                                                       | RenderFragment              | null                                  |
| GroupSeparator              | Defines the thousand grouping separator character.                                                                                                                                                                                                                                                                         | string                      |                                       |
| GroupSpacing                | Defines how many numbers should be grouped together (usually for the thousand separator).                                                                                                                                                                                                                                  | string                      | "3"                                   |
| Immediate                   | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                                                                                                                                       | bool?                       | null                                  |
| Max                         | The maximum value to accept for this input.                                                                                                                                                                                                                                                                                | TValue                      | null                                  |
| Min                         | The minimum value to accept for this input.                                                                                                                                                                                                                                                                                | TValue                      | null                                  |
| MinMaxLimitsOverride        | Override the minimum and maximum limits.Possible values:Ignore, DoNotOverride, Ceiling, Floor                                                                                                                                                                                                                              | NumericMinMaxLimitsOverride | NumericMinMaxLimitsOverride.Ignore    |
| ModifyValueOnWheel          | Determine if the element value can be incremented / decremented with the mouse wheel.                                                                                                                                                                                                                                      | bool                        | false                                 |
| Pattern                     | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                                                                                                                                                                                                 | string                      |                                       |
| Placeholder                 | Sets the placeholder for the empty text.                                                                                                                                                                                                                                                                                   | string                      |                                       |
| Plaintext                   | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                                                                                                                                                                       | bool                        | false                                 |
| ReadOnly                    | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                                                                                                                               | bool                        | false                                 |
| RoundingMethod              | Method used for rounding decimal values.Possible values:HalfUpSymmetric, HalfUpAsymmetric, HalfDownSymmetric, HalfDownAsymmetric, HalfEvenBankersRounding, UpRoundAwayFromZero, DownRoundTowardZero, ToCeilingTowardPositiveInfinity, ToFloorTowardNegativeInfinity, ToNearest05, ToNearest05Alt, UpToNext05, DownToNext05 | NumericRoundingMethod       | NumericRoundingMethod.HalfUpSymmetric |
| SelectAllOnFocus            | If true, selects all the text entered in the input field once it receives the focus.                                                                                                                                                                                                                                       | bool                        | false                                 |
| ShowStepButtons             | If true, step buttons will be visible.                                                                                                                                                                                                                                                                                     | bool?                       | null                                  |
| Size                        | Sets the size of the input control.                                                                                                                                                                                                                                                                                        | Size?                       | null                                  |
| Step                        | Specifies the interval between valid values.                                                                                                                                                                                                                                                                               | decimal?                    | 1                                     |
| TabIndex                    | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                                                                                                              | int?                        | null                                  |
| Value                       | Gets or sets the value inside the input field.                                                                                                                                                                                                                                                                             | TValue                      | null                                  |
| ValueExpression             | Gets or sets an expression that identifies the value.                                                                                                                                                                                                                                                                      | Expression<Func<TValue>>    | null                                  |
| VisibleCharacters           | The size attribute specifies the visible width, in characters, of an input element. See w3schools.com.                                                                                                                                                                                                                     | int?                        | null                                  |
| WheelOn                     | Used in conjonction with the NumericPicker.ModifyValueOnWheel option, defines when the wheel event will increment or decrement the element value, either when the element is focused, or hovered.Possible values:Focus, Hover                                                                                              | NumericWheelOn              | NumericWheelOn.Focus                  |

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
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 