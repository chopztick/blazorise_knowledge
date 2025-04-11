# Blazorise Select component

Selects allow you to choose one or more items from a dropdown menu.

&lt;Select&gt; components are used for collecting user provided information from a list of options.

## Structure

- &lt; Select&gt; The main input.
- &lt;Select&gt; The main input.
    - &lt;SelectItem&gt; The select item, used for defining the options.
    - &lt;SelectGroup&gt; The select group, used for grouping items.

Select and SelectItem are generic components and they support all of the basic value
    types line int, string, enum, etc. Nullable types are also supported. Since they are generic component they also
    come with some special rules that must be followed:

- Value type must be known. When using member variable on bind-* or SelectedValue attributes, the value type
        will be recognized automatically. Otherwise you must use TValue to define it eg (TValue=”int”).
- Value type must be the same in both Select and SelectItem.
- String values must be defined with special syntax eg. @("hello"), see
        #7785

When dealing with a TValue of an enum type, you should be mindfull of your javascript serializer settings. As that will affect the correct handling of this type by the  as it will need to javascript interop the enum value as a string.
        Applying the attribute  to your enum should allow it to be properly bound.

## Examples

### Basic

```
<Select TValue="int">
    <SelectItem Value="1">One</SelectItem>
    <SelectItem Value="2">Two</SelectItem>
    <SelectItem Value="3">Three</SelectItem>
    <SelectItem Value="4">Four</SelectItem>
</Select>
```

### Multiple

Add the  attribute to allow more than one option to be selected.

```
<Select TValue="int" Multiple>
    <SelectItem Value="1">One</SelectItem>
    <SelectItem Value="2">Two</SelectItem>
    <SelectItem Value="3">Three</SelectItem>
    <SelectItem Value="4">Four</SelectItem>
</Select>
```

### Groups

You can also group items into categories for better user experience.

```
<Select TValue="int">
    <SelectGroup Label="Group 1">
        <SelectItem Value="1">One</SelectItem>
        <SelectItem Value="2">Two</SelectItem>
    </SelectGroup>
    <SelectGroup Label="Group 2">
        <SelectItem Value="3">Three</SelectItem>
        <SelectItem Value="4">Four</SelectItem>
    </SelectGroup>
</Select>
```

## Binding

The process is basically the same for the single and for multiple select. The only difference is that
    SelectedValue attribute is used for single select mode, and SelectedValues attribute
    is used for multi-selection. Keep in mind that Multiple must be set to true for multi-selection to work properly.

The  attribute is required on the . Otherwise the  will not behave as expected.

### Two-way binding

By using  attribute the selected item value will be automatically assigned to the member variable.

```
<Select @bind-SelectedValue="@selectedValue">
    <SelectItem Value="1">One</SelectItem>
    <SelectItem Value="2">Two</SelectItem>
    <SelectItem Value="3">Three</SelectItem>
    <SelectItem Value="4">Four</SelectItem>
</Select>
```

```
@code{
    int selectedValue;
}
```

### Manual event binding

When using the event , you also must define the  attribute.

```
<Select TValue="int" SelectedValue="@selectedValue" SelectedValueChanged="@OnSelectedValueChanged">
    <SelectItem Value="1">One</SelectItem>
    <SelectItem Value="2">Two</SelectItem>
    <SelectItem Value="3">Three</SelectItem>
    <SelectItem Value="4">Four</SelectItem>
</Select>
```

```
@code{
    int selectedValue;

    Task OnSelectedValueChanged( int value )
    {
        selectedValue = value;
        Console.WriteLine( selectedValue );

        return Task.CompletedTask;
    }
}
```

## Best Practices

### Set a Default Value

When applicable, set the most common choice as the default value.

### Do Not Use as a Menu

Select is an input field component, not a generic menu component. Use Dropdown to create overlays for actions.

## API

### Parameters

#### Select

| Parameter                | Description                                                                                                   | Type                                    | Default   |
|--------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------|-----------|
| Autofocus                | Set's the focus to the component after the rendering is done.                                                 | bool                                    | false     |
| ChildContent             | Specifies the content to be rendered inside this Select.                                                      | RenderFragment                          | null      |
| Disabled                 | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.       | bool                                    | false     |
| Feedback                 | Placeholder for validation messages.                                                                          | RenderFragment                          | null      |
| Loading                  | Gets or sets loading property.                                                                                | bool                                    | false     |
| MaxVisibleItems          | Specifies how many options should be shown at once.                                                           | int?                                    | null      |
| Multiple                 | Specifies that multiple items can be selected.                                                                | bool                                    | false     |
| ReadOnly                 | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                  | bool                                    | false     |
| SelectedValue            | Gets or sets the selected item value.                                                                         | TValue                                  | null      |
| SelectedValueExpression  | Gets or sets an expression that identifies the selected value.                                                | Expression<Func<TValue>>                | null      |
| SelectedValues           | Gets or sets the multiple selected item values.                                                               | IReadOnlyList<TValue>                   | null      |
| SelectedValuesExpression | Gets or sets an expression that identifies the selected value.                                                | Expression<Func<IReadOnlyList<TValue>>> | null      |
| Size                     | Sets the size of the input control.                                                                           | Size?                                   | null      |
| TabIndex                 | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                                    | null      |

#### SelectItem

| Parameter    | Description                                                     | Type           | Default   |
|--------------|-----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this SelectItem.    | RenderFragment | null      |
| Disabled     | Disable the item from mouse click.                              | bool           | false     |
| Hidden       | Hide the item from the list so it can be used as a placeholder. | bool           | false     |
| Value        | Gets or sets the item value.                                    | TValue         | null      |

#### SelectGroup

| Parameter    | Description                                                   | Type           | Default   |
|--------------|---------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this SelectGroup. | RenderFragment | null      |
| Label        | Gets or sets the group label.                                 | string         |           |

### Events

#### Select

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                                 |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>        |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                         |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>        |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>        |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs>     |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs>     |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs>     |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>        |
| SelectedValueChanged  | Occurs when the selected item value has changed.                                                                                                                                                                                                                                       | EventCallback<TValue>                |
| SelectedValuesChanged | Occurs when the selected items value has changed (only when Select.Multiple==true).                                                                                                                                                                                                    | EventCallback<IReadOnlyList<TValue>> |

### Methods

#### Select

| Method        | Description                                                                                  | Return   | Parameters           |
|---------------|----------------------------------------------------------------------------------------------|----------|----------------------|
| ContainsValue | Indicates if Select contains the provided item value.                                        | bool     | TValue value         |
| Focus         | Sets the focus on the underline element.                                                     | Task     | bool scrollToElement |
| Revalidate    | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task     |                      |

###### On this page

#### 

## 