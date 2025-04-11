# Blazorise ColorEdit component

The ColorEdit allow the user to select a color.

This component works with standard &lt;input type="color"&gt; elements. That is, the browser will control the look and feel, which may differ between Chrome, Firefox, and Edge.

## Examples

### Basic

In this example for Blazorise, the  component is utilized to provide a color selection interface. It's bound to a  variable via the  directive. Initially set to red (, this  automatically updates to reflect the user's color selection made through the  component, showcasing a straightforward way to integrate color picking functionality into a Blazor application.

```
<ColorEdit @bind-Color="@colorValue" />
```

```
@code {
    string colorValue = "#ff0000";
}
```

### Sizes

In the provided example, two  components in a Blazorise application are showcased, each with a distinct  attribute. The first  is configured with , making it smaller in appearance, and the second is set with , resulting in a larger size. This demonstrates the flexibility of the  component in Blazorise, where the Size attribute can be adjusted to control the component's display size according to the application's design requirements.

```
<Field>
    <ColorEdit Color="#888888" Size="Size.Small" />
</Field>
<Field>
    <ColorEdit Color="#444444" Size="Size.Large" />
</Field>
```

### Disabled

In this Blazorise example, the  component is demonstrated with the  attribute. The addition of the  attribute renders the  component non-interactive, meaning the user will not be able to change the color value presented. This is useful in scenarios where you want to display a color but prevent any user interaction, such as in view-only forms or to maintain consistency in certain UI states.

```
<ColorEdit Color="#888888" Disabled />
```

## API

### Parameters

| Parameter       | Description                                                                                                   | Type                     | Default   |
|-----------------|---------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| Autofocus       | Set's the focus to the component after the rendering is done.                                                 | bool                     | false     |
| ChildContent    | Specifies the content to be rendered inside this ColorEdit.                                                   | RenderFragment           | null      |
| Color           | Gets or sets the input color value.                                                                           | string                   |           |
| ColorExpression | Gets or sets an expression that identifies the color value.                                                   | Expression<Func<string>> | null      |
| Disabled        | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                     | false     |
| Feedback        | Placeholder for validation messages.                                                                          | RenderFragment           | null      |
| ReadOnly        | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                     | false     |
| Size            | Sets the size of the input control.                                                                           | Size?                    | null      |
| TabIndex        | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                     | null      |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                             |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>    |
| ColorChanged          | Occurs when the color has changed.                                                                                                                                                                                                                                                     | EventCallback<string>            |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                     |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>    |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs> |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs> |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs> |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>    |

### Methods

| Method     | Description                                                                                  | Return   | Parameters           |
|------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| Select     | Select all text in the underline component.                                                  | Task     | bool focus           |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 