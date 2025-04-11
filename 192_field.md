# Blazorise Field component

A generic container used to properly layout input elements on a form.

The &lt;Field&gt; is a container for input components such as TextEdit, Select, DateEdit,
    Check, MemoEdit, and optionally for Button. Structure is very simple:

- &lt; Field&gt; the main container.
- &lt;Field&gt; the main container.
    - &lt;FieldLabel&gt; used for the label of the field.
    - &lt;FieldBody&gt; the container for the input control.
    - &lt;FieldHelp&gt; used for the help text.
- &lt;Fields&gt; container used to group several Field components

It is recommended to always place input components inside of a field. That way you will keep the right spacing
    and arrangement between input controls.

## Examples

### Basic

To properly structure your form you just need to place an input inside of a Field.

```
<Field>
    <TextEdit Placeholder="Name" />
</Field>
```

### Label

An input field should generally have a label for identifying it. Labels should be clear, concise, and written in sentence case. Avoid unclear and verbose language. Use  to provide more guidance.

```
<Field>
    <FieldLabel>Email address</FieldLabel>
    <TextEdit Placeholder="Enter email" />
</Field>
```

### Helper

Helpers provide information when needed so that end users can fill in a form or field without errors. They are helpful, for example, when the field requires a specific format. Helpers typically consist of plain text but HTML and other components are also supported.

```
<Fields>
    <Field>
        <FieldLabel>Phone number</FieldLabel>
        <TextEdit>
            <FieldHelp>Include country and area prefixes</FieldHelp>
        </TextEdit>
    </Field>
    <Field>
        <FieldLabel>Password</FieldLabel>
        <TextEdit>
            <FieldHelp>Password strength: <Text TextColor="TextColor.Danger">weak</Text></FieldHelp>
        </TextEdit>
    </Field>
</Fields>
```

### Read-Only

Set a field as read-only when the content needs to be accessible but not editable. Read-only elements cannot be edited, but they are in the tabbing order and can thus receive focus. The contents of a read-only input can be selected and copied.

```
<Field>
    <FieldLabel>Read-Only</FieldLabel>
    <TextEdit Text="Value" ReadOnly />
</Field>
```

### Disabled

Disable a field to mark it as unavailable. The disabled state is used for fields that are not editable and do not need to be readable. Disabled elements cannot be focused and may be inaccessible to assistive technologies like screen readers.

Disabling can be preferable to hiding an element to prevent changes in layout when the element’s visibility changes, and to make users aware of its existence even when currently unavailable.

If the user needs to be able to read (or copy) the value, use read-only instead.

```
<Field>
    <FieldLabel>Disabled</FieldLabel>
    <TextEdit Text="Value" Disabled />
</Field>
```

### Horizontal field

When using horizontal field you must place input controls inside of the FieldBody tag and also set the ColumnSize to define the actual sizes of the body and a label.

When using a Check component as input control, it has to be horizontally aligned using with Margin="Margin.IsAuto".

```
<Field Horizontal>
    <FieldLabel ColumnSize="ColumnSize.Is2">Name</FieldLabel>
    <FieldBody ColumnSize="ColumnSize.Is10">
        <TextEdit Placeholder="Some text value..." />
    </FieldBody>
</Field>
<Field Horizontal>
    <FieldLabel ColumnSize="ColumnSize.Is2">Check me</FieldLabel>
    <FieldBody ColumnSize="ColumnSize.Is10" Margin="Margin.IsAuto">
        <Check TValue="bool" />
    </FieldBody>
</Field>
```

### Visibility

Use  attribute to hide a field while still preserving it’s space.

```
<Field Visibility="Visibility.Invisible">
    <TextEdit />
</Field>
```

### Fields

component is used to group multiple  components. For example if you need to group
        fields into columns you must use fields component.

```
<Fields>
    <Field ColumnSize="ColumnSize.Is6.OnDesktop">
        <FieldLabel>City</FieldLabel>
        <TextEdit />
    </Field>
    <Field ColumnSize="ColumnSize.Is4.OnDesktop">
        <FieldLabel>State</FieldLabel>
        <Select TValue="string">
        </Select>
    </Field>
    <Field ColumnSize="ColumnSize.Is2.OnDesktop">
        <FieldLabel>Zip</FieldLabel>
        <TextEdit />
    </Field>
</Fields>
```

### Validation Indicator

In Blazorise, you can take advantage of the  feature on a FieldLabel to automatically signal required input fields. By using this feature, an indicator is automatically displayed next to the label, thereby making it clear to the user that the corresponding input is required. It's a practical tool for enhancing user interface design and improving form usability. This feature enhances user understanding of the form requirements, helping to make form interactions more intuitive.

```
<Field>
    <FieldLabel RequiredIndicator>
        Name
    </FieldLabel>
    <FieldBody>
        <TextEdit Placeholder="Name" />
    </FieldBody>
</Field>
```

## Best Practices

### Do

Use Field to add a label and validation message to form controls.
Use Field to label other unlabeled controls like ProgressBar.

### Don't

Avoid including both a validation message and hint text.
Don't add multiple controls as a child of a single Field. The label is only associated with one control.

## API

### Parameters

#### Field

| Parameter      | Description                                                                                                                                                        | Type           | Default                |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|------------------------|
| ChildContent   | Specifies the content to render inside this Field.Remarks Use this property to define custom child elements or components to be displayed within the column.       | RenderFragment | null                   |
| ColumnSize     | Defines the sizing configuration for the column, supporting responsive layouts and custom size definitions.                                                        | IFluentColumn  | null                   |
| Horizontal     | Determines whether the form controls should be aligned horizontally, as in a horizontal form layout.                                                               | bool           | false                  |
| JustifyContent | Defines how the container's items are aligned along the main axis when there is extra space available.Possible values:Default, Start, End, Center, Between, Around | JustifyContent | JustifyContent.Default |

#### FieldLabel

| Parameter         | Description                                                                                                                                                       | Type           | Default             |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|---------------------|
| ChildContent      | Specifies the content to render inside this FieldLabel.Remarks Use this property to define custom child elements or components to be displayed within the column. | RenderFragment | null                |
| ColumnSize        | Defines the sizing configuration for the column, supporting responsive layouts and custom size definitions.                                                       | IFluentColumn  | null                |
| For               | Gets or sets the ID of an element that this label belongs to.                                                                                                     | string         |                     |
| RequiredIndicator | If defined, a required indicator will be shown next to the label.                                                                                                 | bool           | false               |
| Screenreader      | Defines the visibility for screen readers.Possible values:Always, Only, OnlyFocusable                                                                             | Screenreader   | Screenreader.Always |

#### Fields

| Parameter    | Description                                                                                                                                                   | Type           | Default   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to render inside this Fields.Remarks Use this property to define custom child elements or components to be displayed within the column. | RenderFragment | null      |
| ColumnSize   | Defines the sizing configuration for the column, supporting responsive layouts and custom size definitions.                                                   | IFluentColumn  | null      |
| Help         | Sets the field help-text positioned bellow the field.                                                                                                         | string         |           |
| Label        | Sets the field label.                                                                                                                                         | string         |           |

###### On this page

#### 

## 