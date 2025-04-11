# Blazorise TextEdit component

The TextEdit allows the user to input and edit text.

&lt;TextEdit&gt; fields components are used for collecting user provided information.

## Examples

### Basic

```
<TextEdit />
```

### Placeholder

```
<TextEdit Placeholder="Some text value..." />
```

### Static text

Static text removes the background, border, shadow, and horizontal padding, while maintaining the
        vertical spacing so you can easily align the input in any context, like a horizontal form.

```
<TextEdit Plaintext />
```

### Disabled

A disabled input element is unusable and un-clickable.

```
<TextEdit Disabled />
```

### ReadOnly

If you use the read-only attribute, the input text will look similar to a normal one, but is not editable.

```
<TextEdit ReadOnly />
```

### Sizing

Sets the heights of input elements.

```
<Field>
    <TextEdit Size="Size.Small" />
</Field>
<Field>
    <TextEdit Size="Size.Large" />
</Field>
```

### Pattern

Use pattern attribute to specify regular expression that will be used while validating the input text value.

Pattern does not match!

```
<Validation UsePattern>
    <TextEdit Pattern="[A-Za-z]{3}">
        <Feedback>
            <ValidationError>Pattern does not match!</ValidationError>
        </Feedback>
    </TextEdit>
</Validation>
```

### EditMask

Edit masks are used to prevent user from entering an invalid values and when entered string must match
        a specific format. For example you can limit input to only accept numeric string, date string or if you
        want full control you can use RegEx format.

```
<Fields>
    <Field ColumnSize="ColumnSize.Is6.OnDesktop.Is12.OnMobile">
        <FieldLabel>
            Text only
        </FieldLabel>
        <FieldBody>
            <TextEdit MaskType="MaskType.RegEx" EditMask="^[a-zA-Z ]*$" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.Is6.OnDesktop.Is12.OnMobile">
        <FieldLabel>
            Numbers only
        </FieldLabel>
        <FieldBody>
            <TextEdit MaskType="MaskType.RegEx" EditMask="^(\d+(.\d{0,2})?|.?\d{1,2})$" />
        </FieldBody>
    </Field>
</Fields>
```

### Roles

Use Role to define type of text value.

```
<Fields>
    <Field ColumnSize="ColumnSize.Is6.OnDesktop.Is12.OnMobile">
        <FieldLabel>
            Email
        </FieldLabel>
        <FieldBody>
            <TextEdit Role="TextRole.Email" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.Is6.OnDesktop.Is12.OnMobile">
        <FieldLabel>
            Password
        </FieldLabel>
        <FieldBody>
            <TextEdit Role="TextRole.Password" autocomplete="new-password" />
        </FieldBody>
    </Field>
</Fields>
```

## Binding

### Two-way binding

By using  attribute the text will be automatically assigned to the member variable.

```
<TextEdit @bind-Text="@name" />
```

```
@code{
    string name;
}
```

### Manual event binding

When using the event , you also must define the  value attribute.

```
<TextEdit Text="@name" TextChanged="@OnNameChanged" />
```

```
@code{
    string name;

    Task OnNameChanged( string value )
    {
        name = value;

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

## Best Practices

### Prevent autocomplete

When working with email and password fields, in some cases browsers might automatically autofill them with the values from user system. To prevent it you can define an autocomplete attribute, eg. autocomplete="new-password" on an input field.

## API

### Parameters

| Parameter         | Description                                                                                                                                                                 | Type                     | Default            |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------|
| Autofocus         | Set's the focus to the component after the rendering is done.                                                                                                               | bool                     | false              |
| ChildContent      | Specifies the content to be rendered inside this TextEdit.                                                                                                                  | RenderFragment           | null               |
| Color             | Sets the input text color.                                                                                                                                                  | Color                    | Color.Default      |
| Debounce          | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                               | bool?                    | null               |
| DebounceInterval  | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                           | int?                     | null               |
| Disabled          | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                     | bool                     | false              |
| EditMask          | A string representing a edit mask expression.                                                                                                                               | string                   |                    |
| Feedback          | Placeholder for validation messages.                                                                                                                                        | RenderFragment           | null               |
| Immediate         | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                        | bool?                    | null               |
| InputMode         | Hints at the type of data that might be entered by the user while editing the element or its contents.Possible values:None, Text, Tel, Url, Email, Numeric, Decimal, Search | TextInputMode            | TextInputMode.None |
| MaskType          | Specify the mask type used by the editor.Possible values:None, Numeric, DateTime, RegEx                                                                                     | MaskType                 | MaskType.None      |
| MaxLength         | Specifies the maximum number of characters allowed in the input element.                                                                                                    | int?                     | null               |
| Pattern           | The pattern attribute specifies a regular expression that the input element's value is checked against on form validation.                                                  | string                   |                    |
| Placeholder       | Sets the placeholder for the empty text.                                                                                                                                    | string                   |                    |
| Plaintext         | Sets the class to remove the default form field styling and preserve the correct margin and padding.                                                                        | bool                     | false              |
| ReadOnly          | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                | bool                     | false              |
| Role              | Defines the role of the input text.Possible values:Text, Email, Password, Url, Search, Telephone                                                                            | TextRole                 | TextRole.Text      |
| Size              | Sets the size of the input control.                                                                                                                                         | Size?                    | null               |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                               | int?                     | null               |
| Text              | Gets or sets the text inside the input field.                                                                                                                               | string                   |                    |
| TextExpression    | Gets or sets an expression that identifies the text value.                                                                                                                  | Expression<Func<string>> | null               |
| VisibleCharacters | The size attribute specifies the visible width, in characters, of an input element. See w3schools.com.                                                                      | int?                     | null               |

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