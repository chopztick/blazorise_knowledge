# Blazorise NumericEdit component

A native numeric &lt;input&gt; component built around the &lt;input type="number"&gt;.

Use &lt;NumericEdit&gt; to have a field for any kind of numeric values. All basic types are supported, including nullable types (int, long, float, double, decimal, etc.).

Being built around native type="number" input element, the NumericEdit component in Blazorise has certain inherent limitations due to its reliance on native browser functionalities for numeric inputs. One such limitation is the handling of decimal values; for instance, inputting "0.0" may result in the component rounding the value to "0". This occurs because the browser considers "0.0" as a complete value, which triggers an onchange event. Internally, the component, not knowing the exact number of decimals intended, rounds the value and subsequently triggers a ValueChanged event. This, in turn, prompts a refresh, causing Blazor to redraw the NumericEdit component, which updates the value and the caret position.

Additionally, due to the component using the native type="number" partial values cannot be retrieved mid-entry. This means that constraints on the Value are only checked upon the blur event, allowing for the detection and handling of invalid values without interrupting the user's input process. To mitigate these issues, users could consider setting Immediate="false" to ensure the value is only submitted once focus is lost, or alternatively, use the NumericPicker component as a substitute.

## Examples

### Basic

```
<NumericEdit @bind-Value="@value" />
```

```
@code {
    decimal? value = 123;
}
```

### Generic type

Since  is a generic component you will have to specify the exact data type for the value.
        Most of the time it will be recognized automatically when you set the  attribute, but if
        not you will just use the  attribute and define the type manually eg.

```
<NumericEdit TValue="decimal?" @bind-Value="@value" />
```

```
@code {
    decimal? value = 123;
}
```

## API

### Parameters

| Parameter         | Description                                                                                                                                          | Type                     | Default       |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|---------------|
| Autofocus         | Set's the focus to the component after the rendering is done.                                                                                        | bool                     | false         |
| ChildContent      | Specifies the content to be rendered inside this NumericEdit.                                                                                        | RenderFragment           | null          |
| Color             | Sets the input text color.                                                                                                                           | Color                    | Color.Default |
| Culture           | Helps define the language of an element. See w3schools.com.                                                                                          | string                   |               |
| Debounce          | If true the entered text will be slightly delayed before submitting it to the internal value.                                                        | bool?                    | null          |
| DebounceInterval  | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                    | int?                     | null          |
| Disabled          | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                              | bool                     | false         |
| Feedback          | Placeholder for validation messages.                                                                                                                 | RenderFragment           | null          |
| Immediate         | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate. | bool?                    | null          |
| Max               | The maximum value to accept for this input.                                                                                                          | TValue                   | null          |
| Min               | The minimum value to accept for this input.                                                                                                          | TValue                   | null          |
| Pattern           | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                           | string                   |               |
| Placeholder       | Sets the placeholder for the empty text.                                                                                                             | string                   |               |
| Plaintext         | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                 | bool                     | false         |
| ReadOnly          | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                         | bool                     | false         |
| Size              | Sets the size of the input control.                                                                                                                  | Size?                    | null          |
| Step              | Specifies the interval between valid values.                                                                                                         | decimal?                 | 1             |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                        | int?                     | null          |
| Value             | Gets or sets the value inside the input field.                                                                                                       | TValue                   | null          |
| ValueExpression   | Gets or sets an expression that identifies the value.                                                                                                | Expression<Func<TValue>> | null          |
| VisibleCharacters | The size attribute specifies the visible width, in characters, of an input element. See w3schools.com.                                               | int?                     | null          |

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
| ValueChanged          | Occurs after the value has changed.Remarks This will be converted to EventCallback once the Blazor team fix the error for generic components. See github.com/aspnet.                                                                                                                   | EventCallback<TValue>            |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 