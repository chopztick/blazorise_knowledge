# Blazorise Dropdown component

Dropdowns expose additional content that "drops down" in a menu.

Dropdowns are toggleable, contextual overlays for displaying lists of links and actions in a dropdown menu format.

Dropdowns are designed to work well with menus to provide a list of options the user can select from. However, dropdowns can also be used in lower-level applications (e.g. color picker and select). The API gives you complete control over showing, hiding, and positioning the menu.

- Dropdown the main container.
- Dropdown the main container.
    - &lt;DropdownToggle&gt; the button that toggles the dropdown menu.
    - &lt; DropdownMenu&gt; the container for the dropdown menu. Hidden by default.
    - &lt;DropdownMenu&gt; the container for the dropdown menu. Hidden by default.
        - &lt;DropdownItem&gt; a clickable item in the dropdown menu.
        - &lt;DropdownDivider&gt; a horizontal line to separate dropdown items.
        - &lt;DropdownHeader&gt; a non-clickable header in the dropdown menu.

### Dropdown

```
<Dropdown>
    <DropdownToggle Color="Color.Primary">
        Dropdown
    </DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Action</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Another Action</DropdownItem>
    </DropdownMenu>
</Dropdown>
```

### Dropdown checkboxes

Set Checkbox to true to render a checkbox by each dropdown item.

```
<Dropdown>
    <DropdownToggle Color="Color.Primary">
        Dropdown With Checkboxes
    </DropdownToggle>
    <DropdownMenu>
        <DropdownItem ShowCheckbox>Checkbox</DropdownItem>
        <DropdownDivider />
        <DropdownItem ShowCheckbox>Another Checkbox</DropdownItem>
        <DropdownItem ShowCheckbox Disabled>Checkbox Disabled</DropdownItem>
        <DropdownItem>Action</DropdownItem>
    </DropdownMenu>
</Dropdown>
```

### Split Dropdown

Just add another Button to have a split dropdown.

```
<Dropdown>
    <Button Color="Color.Primary">Split Dropdown</Button>
    <DropdownToggle Color="Color.Primary" Split />
    <DropdownMenu>
        <DropdownItem>Action</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Another Action</DropdownItem>
    </DropdownMenu>
</Dropdown>
```

### Show Menu

By default a dropdown toggle will show and hide a dropdown menu without the need to do it manually. In case you need to control the menu programmatically you have to use the Dropdown reference.

```
<Dropdown @ref="dropdown" Display="Display.InlineBlock">
    <DropdownToggle Color="Color.Primary">Menu</DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Action</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Another Action</DropdownItem>
    </DropdownMenu>
</Dropdown>

<Button Clicked="@ShowMenu" Color="Color.Secondary">Show Menu</Button>
```

```
@code {
    Dropdown dropdown;

    Task ShowMenu()
    {
        return dropdown.Show();
    }
}
```

### Scrollable Menu

By default the menu will show all items. If you want to add the scrolling to the menu you just need to define the
        menu  parameter.

```
<Dropdown Display="Display.InlineBlock">
    <DropdownToggle Color="Color.Primary">Menu</DropdownToggle>
    <DropdownMenu MaxMenuHeight="100px">
        <DropdownItem>Action</DropdownItem>
        <DropdownItem>Action 2</DropdownItem>
        <DropdownItem>Action 3</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Another Action</DropdownItem>
        <DropdownItem>Another Action 2</DropdownItem>
    </DropdownMenu>
</Dropdown>
```

### Nested submenus

By adding a few more Dropdowns you can add extra levels of submenu to your dropdown. You can apply this to the dropdown in a simple button or within the navbar.

```
<Dropdown>
    <DropdownToggle Color="Color.Primary">Level 1</DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Item 1.1</DropdownItem>
        <Dropdown>
            <DropdownToggle>Level 2</DropdownToggle>
            <DropdownMenu>
                <DropdownItem>Item 2.1</DropdownItem>
                <DropdownItem>Item 2.2</DropdownItem>
                <Dropdown>
                    <DropdownToggle>Level 3</DropdownToggle>
                    <DropdownMenu>
                        <DropdownItem>Item 3.1</DropdownItem>
                        <DropdownItem>Item 3.2</DropdownItem>
                        <Dropdown>
                            <DropdownToggle>Level 4</DropdownToggle>
                            <DropdownMenu>
                                <DropdownItem>Item 4.1</DropdownItem>
                                <DropdownItem>Item 4.2</DropdownItem>
                            </DropdownMenu>
                        </Dropdown>
                    </DropdownMenu>
                </Dropdown>
            </DropdownMenu>
        </Dropdown>
    </DropdownMenu>
</Dropdown>
```

### Nested submenus with direction

Nested dropdowns with the manual  is also supported.

```
<Dropdown>
    <DropdownToggle Color="Color.Primary">Level 1</DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Item 1.1</DropdownItem>
        <Dropdown Direction="Direction.Up">
            <DropdownToggle>Level 2</DropdownToggle>
            <DropdownMenu>
                <DropdownItem>Item 2.1</DropdownItem>
                <DropdownItem>Item 2.2</DropdownItem>
                <Dropdown Direction="Direction.Down">
                    <DropdownToggle>Level 3</DropdownToggle>
                    <DropdownMenu>
                        <DropdownItem>Item 3.1</DropdownItem>
                        <DropdownItem>Item 3.2</DropdownItem>
                        <Dropdown Direction="Direction.Start">
                            <DropdownToggle>Level 4</DropdownToggle>
                            <DropdownMenu>
                                <DropdownItem>Item 4.1</DropdownItem>
                                <DropdownItem>Item 4.2</DropdownItem>
                            </DropdownMenu>
                        </Dropdown>
                    </DropdownMenu>
                </Dropdown>
            </DropdownMenu>
        </Dropdown>
    </DropdownMenu>
</Dropdown>
```

## Best Practices

- Dropdown should not be used for navigation. Use tabs for switching between content, or anchor elements for regular navigation.
- Dropdown is not an input field. Use Select, or Radio Button instead.

## Functions

| Name     | Description                               |
|----------|-------------------------------------------|
| Show()   | Show the dropdown menu.                   |
| Hide()   | Hides the dropdown menu.                  |
| Toggle() | Switches the visibility of dropdown menu. |

## API

### Parameters

#### Dropdown

| Parameter            | Description                                                                                                                                                                             | Type                     | Default                        |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------------------|
| ChildContent         | Specifies the content to be rendered inside this Dropdown.                                                                                                                              | RenderFragment           | null                           |
| Direction            | Dropdown-menu slide direction.Possible values:Default, Down, Up, End, Start                                                                                                             | Direction                | Direction.Default              |
| Disabled             | If true, dropdown would not react to button click.                                                                                                                                      | bool                     | false                          |
| DropdownMenuTargetId | Provides an alternative, or custom anchor element id for the dropdown menu.     This is useful when you want the dropdown menu to be anchored from a different element than the toggle. | string                   |                                |
| PositionStrategy     | Defines the positioning strategy of the dropdown menu as a 'floating' element.Possible values:Absolute, Fixed                                                                           | DropdownPositionStrategy | DropdownPositionStrategy.Fixed |
| RightAligned         | If true, a dropdown menu will be right aligned.                                                                                                                                         | bool                     | false                          |
| Visible              | If true, a dropdown menu will be visible.                                                                                                                                               | bool                     | false                          |

#### DropdownMenu

| Parameter     | Description                                                 | Type           | Default   |
|---------------|-------------------------------------------------------------|----------------|-----------|
| ChildContent  | Specifies the content to be rendered inside this Container. | RenderFragment | null      |
| MaxMenuHeight | Sets the maximum height of the dropdown menu.               | string         |           |

#### DropdownItem

| Parameter    | Description                                                             | Type           | Default   |
|--------------|-------------------------------------------------------------------------|----------------|-----------|
| Active       | Indicate the currently active item.                                     | bool           | false     |
| Checked      | Tracks the Checked state whenever the DropdownItem is in checkbox mode. | bool           | false     |
| ChildContent | Specifies the content to be rendered inside this DropdownItem.          | RenderFragment | null      |
| Disabled     | Indicate the currently disabled item.                                   | bool           | false     |
| ShowCheckbox | The dropdown renders a checkbox.                                        | bool           | false     |
| Value        | Holds the item value.                                                   | object         | null      |

#### DropdownToggle

| Parameter         | Description                                                                                                   | Type           | Default       |
|-------------------|---------------------------------------------------------------------------------------------------------------|----------------|---------------|
| ChildContent      | Specifies the content to be rendered inside this DropdownToggle.                                              | RenderFragment | null          |
| Color             | Gets or sets the dropdown color.                                                                              | Color          | Color.Default |
| Disabled          | Makes the toggle element look inactive.                                                                       | bool           | false         |
| Outline           | Button outline.                                                                                               | bool           | false         |
| Size              | Gets or sets the dropdown size.                                                                               | Size?          | null          |
| Split             | Indicates that a toggle should act as a split button.                                                         | bool           | false         |
| TabIndex          | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?           | null          |
| ToggleIconVisible | Gets or sets a value indicating whether the dropdown toggle icon is visible.Remarks Default: True             | bool?          | null          |

### Events

#### Dropdown

| Event          | Description                                            | Type                |
|----------------|--------------------------------------------------------|---------------------|
| VisibleChanged | Occurs after the dropdown menu visibility has changed. | EventCallback<bool> |

#### DropdownItem

| Event          | Description                                                                               | Type                  |
|----------------|-------------------------------------------------------------------------------------------|-----------------------|
| CheckedChanged | Occurs after the Checked state is changed, whenever the DropdownItem is in checkbox mode. | EventCallback<bool>   |
| Clicked        | Occurs when the item is clicked.                                                          | EventCallback<object> |

#### DropdownToggle

| Event   | Description                               | Type                          |
|---------|-------------------------------------------|-------------------------------|
| Clicked | Occurs when the toggle button is clicked. | EventCallback<MouseEventArgs> |

### Methods

#### Dropdown

| Method   | Description                                 | Return   | Parameters                     |
|----------|---------------------------------------------|----------|--------------------------------|
| Show     | Show the dropdown menu.                     | Task     |                                |
| Hide     | Hide the dropdown menu.                     | Task     | bool hideAll                   |
| Toggle   | Toggle the visibility of the dropdown menu. | Task     | string dropdownToggleElementId |

#### DropdownToggle

| Method        | Description                                                    | Return     | Parameters                                                     |
|---------------|----------------------------------------------------------------|------------|----------------------------------------------------------------|
| IsSafeToClose | Returns true of the parent dropdown-menu is safe to be closed. | Task<bool> | string elementId, CloseReason closeReason, bool isChildClicked |
| Close         | Forces the parent dropdown to close the dropdown-menu.         | Task       | CloseReason closeReason                                        |
| Focus         | Sets focus on the input element, if it can be focused.         | Task       | bool scrollToElement                                           |

###### On this page

#### 

## 