# Blazorise MemoEdit component

MemoEdit collect data from the user and allow multiple lines of text.

MemoEdit is an input field component for multi-line text input based on a &lt;textarea&gt; element.

### Basic

```
<MemoEdit Rows="5" />
```

### Tab override

By default a  will lose focus when you press the tab key. If you want to allow tabs to be entered
        you just need to enable it with , and optionally a  parameter.

```
<MemoEdit Rows="5" ReplaceTab TabSize="4" />
```

### Auto size

Unless set to a fixed height, MemoEdit adjusts its height automatically based on its content. The default and minimum height is two rows of text.

```
<MemoEdit Text="@loremipsum" AutoSize />
```

```
@code {
    string loremipsum = @"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vel semper libero. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae.

Proin volutpat, sapien ut facilisis ultricies, eros purus blandit velit, at ultrices mi libero quis ante. Curabitur scelerisque metus et libero convallis consequat. Pellentesque feugiat pulvinar nisl sed pellentesque.";
}
```

## Binding

### Two-way binding

By using  attribute the text will be automatically assigned to the member variable.

```
<MemoEdit @bind-Text="@description" />
```

```
@code{
    string description;
}
```

### Mannual event binding

When using the event , you also must define the  value attribute.

```
<MemoEdit Text="@description" TextChanged="@OnDescriptionChanged" />
```

```
@code{
    string description;

    Task OnDescriptionChanged( string value )
    {
        description = value;

        return Task.CompletedTask;
    }
}
```

## Settings

### Text Changed mode

By default the  event will be raised on every keypress.
        To override default behavior of  event and to disable the change on every
        keypress you must set the  to  on application start.
        After setting it to  the event will be raised only after the input loses focus.

```
public void ConfigureServices( IServiceCollection services )
{
  services
    .AddBlazorise( options =>
    {
      options.Immediate = false;
    } );
}
```

### Text Delay mode

Because of some limitations in Blazor, sometimes there can be problems when  is enabled.
        Basically if you try to type too fast into the text field the caret can jump randomly from current selection
        to the end of the text. To prevent that behaviour you need to enable . Once enabled it will
        slightly delay every value entered into the field to allow the Blazor engine to do it’s thing.
        By default this option is disabled.

```
public void ConfigureServices( IServiceCollection services )
{
  services
    .AddBlazorise( options =>
    {
      options.Debounce = true;
      options.DebounceInterval = 300;
    } );
}
```

All of the options above can also be defined on each  individually.
        Defining them on  will override any global settings.

## API

### Parameters

| Parameter        | Description                                                                                                                                                                                                                  | Type                     | Default   |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| Autofocus        | Set's the focus to the component after the rendering is done.                                                                                                                                                                | bool                     | false     |
| AutoSize         | If true, the textarea will automatically grow in height according to its content.                                                                                                                                            | bool                     | false     |
| ChildContent     | Specifies the content to be rendered inside this MemoEdit.                                                                                                                                                                   | RenderFragment           | null      |
| Debounce         | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                                | bool?                    | null      |
| DebounceInterval | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                            | int?                     | null      |
| Disabled         | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                      | bool                     | false     |
| Feedback         | Placeholder for validation messages.                                                                                                                                                                                         | RenderFragment           | null      |
| Immediate        | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                                         | bool?                    | null      |
| MaxLength        | Specifies the maximum number of characters allowed in the input element.                                                                                                                                                     | int?                     | null      |
| Pattern          | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.Remarks Please be aware that MemoEdit.Pattern on MemoEdit is used only for the validation process. | string                   |           |
| Placeholder      | Sets the placeholder for the empty text.                                                                                                                                                                                     | string                   |           |
| Plaintext        | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                                                                         | bool                     | false     |
| ReadOnly         | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                                 | bool                     | false     |
| ReplaceTab       | If set to true, MemoEdit.ReplaceTab will insert a tab instead of cycle input focus.                                                                                                                                          | bool                     | false     |
| Rows             | Specifies the number lines in the input element.                                                                                                                                                                             | int?                     | null      |
| Size             | Sets the size of the input control.                                                                                                                                                                                          | Size?                    | null      |
| SoftTabs         | If set to true, spaces will be used instead of a tab character                                                                                                                                                               | bool                     | true      |
| TabIndex         | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                | int?                     | null      |
| TabSize          | Defines the number of characters that tab key will override.                                                                                                                                                                 | int                      | 4         |
| Text             | Gets or sets the text inside the input field.                                                                                                                                                                                | string                   |           |
| TextExpression   | Gets or sets an expression that identifies the text value.                                                                                                                                                                   | Expression<Func<string>> | null      |

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
| TextChanged           | Occurs after text has changed.                                                                                                                                                                                                                                                         | EventCallback<string>            |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 