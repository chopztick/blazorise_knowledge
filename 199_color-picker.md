# Blazorise ColorPicker component

The ColorPicker allow the user to select a color using a variety of input methods.

ColorPicker component is based on a Pickr library
    and as such is not a native color input element. That means that unlike ColorEdit which will render &lt;input type="color"&gt;,
    ColorPicker will render span element.

## Examples

### Basic

In this Blazorise example, a  component is bound to a colorValue variable using the  directive. Initially set to red (), the  updates automatically when a user selects a new color through the , demonstrating an interactive color selection tool in a Blazor application.

```
<ColorPicker @bind-Color="@colorValue" />
```

```
@code {
    string colorValue = "#ff0000";
}
```

### Show Hue Slider

In this Blazorise example, the  component is enhanced with a hue slider, as indicated by the  attribute.

```
<ColorPicker @bind-Color="@colorValue" ShowHueSlider />
```

```
@code {
    string colorValue = "#ff00ff";
}
```

## API

### Parameters

| Parameter              | Description                                                                                                                                         | Type                     | Default   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| Autofocus              | Set's the focus to the component after the rendering is done.                                                                                       | bool                     | false     |
| ChildContent           | Specifies the content to be rendered inside this ColorPicker.                                                                                       | RenderFragment           | null      |
| Color                  | Gets or sets the input color value.                                                                                                                 | string                   | "#000000" |
| ColorExpression        | Gets or sets an expression that identifies the color value.                                                                                         | Expression<Func<string>> | null      |
| Disabled               | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                             | bool                     | false     |
| Feedback               | Placeholder for validation messages.                                                                                                                | RenderFragment           | null      |
| HideAfterPaletteSelect | Automatically hides the dropdown menu after a palette color is selected.                                                                            | bool                     | true      |
| Palette                | List a colors below the colorpicker to make it convenient for users to choose from     frequently or recently used colors.                          | string[]                 | new string[]     {         "rgba(244, 67, 54, 1)",         "rgba(233, 30, 99, 0.95)",         "rgba(156, 39, 176, 0.9)",         "rgba(103, 58, 183, 0.85)",         "rgba(63, 81, 181, 0.8)",         "rgba(33, 150, 243, 0.75)",         "rgba(3, 169, 244, 0.7)",         "rgba(0, 188, 212, 0.7)",         "rgba(0, 150, 136, 0.75)",         "rgba(76, 175, 80, 0.8)",         "rgba(139, 195, 74, 0.85)",         "rgba(205, 220, 57, 0.9)",         "rgba(255, 235, 59, 0.95)",         "rgba(255, 193, 7, 1)"     }           |
| PickerLocalizer        | Function used to handle custom localization that will override a default Localization.ITextLocalizer.                                               | TextLocalizerHandler     | null      |
| ReadOnly               | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                        | bool                     | false     |
| ShowCancelButton       | Controls the visibility of the cancel buttons.                                                                                                      | bool                     | true      |
| ShowClearButton        | Controls the visibility of the clear buttons.                                                                                                       | bool                     | true      |
| ShowHueSlider          | Controls the visibility of the hue slider.                                                                                                          | bool                     | false     |
| ShowInputField         | Controls the visibility of the textbox which shows the selected color value.                                                                        | bool                     | true      |
| ShowOpacitySlider      | Controls the visibility of the opacity slider.                                                                                                      | bool                     | true      |
| ShowPalette            | Controls the visibility of the palette below the colorpicker to make it convenient for users to     choose from frequently or recently used colors. | bool                     | true      |
| Size                   | Sets the size of the input control.                                                                                                                 | Size?                    | null      |
| TabIndex               | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                       | int?                     | null      |

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
| SetValue   | Updated the ColorPicker with the new value.                                                  | Task     | string value         |
| Focus      | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 