# Blazorise Addon component

Easily extend form controls by adding text, or buttons on either side of textual inputs, custom selects, and custom file inputs.

## Overview

The &lt;Addon&gt; component is the easiest way to add some structure to forms. Its purpose is to pair
    form controls with a legend or label, and to provide help text and invalid/valid feedback text, as well as
    visual (color) contextual state feedback.

## Structure

- &lt; Addons&gt; main container, used to wrap the input field and the addon content.
- &lt;Addons&gt; main container, used to wrap the input field and the addon content.
    - &lt;Addon&gt; wrapper for addon content, such as labels, buttons, or icons.

To define addon location you have to set the AddonType attribute:

- .Start will place addon on the left side.
- .Body will place it in the middle.
- .End will place it at the right side.

## Examples

### Static label

By incorporating this static label, users are given a precise indication of the expected input, ensuring they enter a suitable username for their account. This Addon design results in a more intuitive and user-friendly interface, making the registration process seamless and efficient.

```
<Addons>
    <Addon AddonType="AddonType.Start">
        <AddonLabel>@@</AddonLabel>
    </Addon>
    <Addon AddonType="AddonType.Body">
        <TextEdit Placeholder="Username" />
    </Addon>
</Addons>
```

### Multiple addons

In this example, an Addon component is used to incorporate multiple labels alongside an input field, enhancing user experience by providing clear guidance and structure.

```
<Addons>
    <Addon AddonType="AddonType.Start">
        <AddonLabel>Start</AddonLabel>
    </Addon>
    <Addon AddonType="AddonType.Body">
        <TextEdit Placeholder="Placeholder" />
    </Addon>
    <Addon AddonType="AddonType.End">
        <AddonLabel>End</AddonLabel>
    </Addon>
</Addons>
```

### Button addon

In this example, we have an Addon component that features a simple button alongside an input field.

Imagine a scenario where users need to enter a numerical value into the input field, such as a quantity for a shopping cart. The Addon component integrates a button labeled "Add" next to the input field. When users enter a quantity and click the "Add" button, the desired item and its corresponding quantity are added to the shopping cart. This Addon design provides a user-friendly interface, allowing for seamless interaction with the input field and button.

```
<Addons>
    <Addon AddonType="AddonType.Body">
        <TextEdit Placeholder="Recipient's username" />
    </Addon>
    <Addon AddonType="AddonType.End">
        <Button Color="Color.Secondary">Button</Button>
    </Addon>
</Addons>
```

### Dropdown addon

Consider a scenario where you have a search input field, and you want to give users the option to select a search category from a Dropdown button before executing the search. This Addon component combines the input field with the Dropdown button for a seamless user experience.

```
<Addons>
    <Addon AddonType="AddonType.Start">
        <Dropdown>
            <DropdownToggle Color="Color.Primary">Dropdown</DropdownToggle>
            <DropdownMenu>
                <DropdownItem>Action</DropdownItem>
                <DropdownItem>Another action</DropdownItem>
                <DropdownItem>Something else here</DropdownItem>
                <DropdownDivider />
                <DropdownItem>Separated link</DropdownItem>
            </DropdownMenu>
        </Dropdown>
    </Addon>
    <Addon AddonType="AddonType.Body">
        <TextEdit />
    </Addon>
</Addons>
```

### Addon with validation

When incorporating input validation within an Addon component, the user interface may become disrupted. This issue arises due to the Addon's distinct HTML and CSS structure, which is designed to accommodate specific elements. Displaying validation error messages within an Addon is one such instance that can cause complications.

In the following example, we will demonstrate a solution to this issue, ensuring that the input validation process within an Addon component functions smoothly without disrupting the user interface. This example will provide a better understanding of how to effectively handle validation errors inside of an Addon.

Enter valid name!

```
<Validation Validator="ValidationRule.IsNotEmpty">
    <Addons>
        <Addon AddonType="AddonType.Body">
            <TextEdit Placeholder="Enter name" />
        </Addon>
        <Addon AddonType="AddonType.End">
            <AddonLabel>This is a label</AddonLabel>
        </Addon>
        <ValidationNone></ValidationNone>
        <ValidationSuccess></ValidationSuccess>
        <ValidationError>Enter valid name!</ValidationError>
    </Addons>
</Validation>
```

## API

### Parameters

#### Addons

| Parameter    | Description                                                    | Type           | Default   |
|--------------|----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this Addons.       | RenderFragment | null      |
| Size         | Changes the size of the elements placed inside of this Addons. | Size?          | null      |

#### Addon

| Parameter    | Description                                                                            | Type           | Default        |
|--------------|----------------------------------------------------------------------------------------|----------------|----------------|
| AddonType    | Defines the location and behaviour of addon container.Possible values:Body, Start, End | AddonType      | AddonType.Body |
| ChildContent | Specifies the content to be rendered inside this Addon.                                | RenderFragment | null           |

###### On this page

#### 

## 