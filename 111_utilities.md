# Utilities

### Spacing

To define spacing between components you have an option to use a fluent-builder pattern. This way you can combine multiple spacings at once.

The following example will set the margins for mobile(xs) and desktop(md) breakpoints:

The same rules can also be applied for paddings.

This example sets the margins for mobile(xs) and desktop(md) breakpoints

```
<Card>
    <CardBody Margin="Margin.Is2.OnMobile.Is5.OnDesktop">
        This example sets the margins for mobile(xs) and desktop(md) breakpoints
    </CardBody>
</Card>
```

### Display

Quickly and responsively toggle the display value of components and more with display utilities.

Hides on screens smaller than lg

```
<Paragraph Display="Display.None.Block.OnFullHD">
    Hides on screens smaller than lg
</Paragraph>
```

### ColumnSize

Similar to the spacing builder you can also define column sizes using the same pattern.

Some content...

```
<Row>
    <Column ColumnSize="ColumnSize.Is4.OnTablet.Is3.OnWidescreen.Is12.OnMobile">
    Some content...    
    </Column>
</Row>
```

### Flex

Quickly manage the layout, alignment, and sizing of grid columns, navigation, components, and more with a full suite of responsive flexbox utilities.

For more complex implementations, custom CSS may be necessary.

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

```
<Div Flex="Flex.AlignItems.Start" Margin="Margin.Is3.FromBottom" Style="@alignItemsFlexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.AlignItems.End" Margin="Margin.Is3.FromBottom" Style="@alignItemsFlexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.AlignItems.Center" Margin="Margin.Is3.FromBottom" Style="@alignItemsFlexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.AlignItems.Baseline" Margin="Margin.Is3.FromBottom" Style="@alignItemsFlexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.AlignItems.Stretch" Margin="Margin.Is3.FromBottom" Style="@alignItemsFlexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
```

```
@code {
    const string ContainerBackgroundColor = "rgba(165, 181, 167,.15)";
    const string ContainerBorderColor = "rgba(165, 181, 167,.15)";

    const string ItemBackgroundColor = "rgba(95, 163, 103,.15)";
    const string ItemBorderColor = "rgba(95, 163, 103,.15)";

    string flexContainerStyle = $"background-color: {ContainerBackgroundColor};border: 1px solid {ContainerBorderColor};";
    string alignItemsFlexContainerStyle = $"background-color: {ContainerBackgroundColor};border: 1px solid {ContainerBorderColor};height: 100px;";

    string flexItemStyle = $"background-color: {ItemBackgroundColor}; border: 1px solid {ItemBorderColor};";
}
```

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

Flex item 1

Flex item 2

Flex item 3

```
<Div Flex="Flex.JustifyContent.Start" Margin="Margin.Is3.FromBottom" Style="@flexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.JustifyContent.End" Margin="Margin.Is3.FromBottom" Style="@flexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.JustifyContent.Center" Margin="Margin.Is3.FromBottom" Style="@flexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.JustifyContent.Between" Margin="Margin.Is3.FromBottom" Style="@flexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
<Div Flex="Flex.JustifyContent.Around" Margin="Margin.Is3.FromBottom" Style="@flexContainerStyle">
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 1
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 2
    </Div>
    <Div Padding="Padding.Is2" Style="@flexItemStyle">
        Flex item 3
    </Div>
</Div>
```

```
@code {
    const string ContainerBackgroundColor = "rgba(165, 181, 167,.15)";
    const string ContainerBorderColor = "rgba(165, 181, 167,.15)";

    const string ItemBackgroundColor = "rgba(95, 163, 103,.15)";
    const string ItemBorderColor = "rgba(95, 163, 103,.15)";

    string flexContainerStyle = $"background-color: {ContainerBackgroundColor};border: 1px solid {ContainerBorderColor};";
    string alignItemsFlexContainerStyle = $"background-color: {ContainerBackgroundColor};border: 1px solid {ContainerBorderColor};height: 100px;";

    string flexItemStyle = $"background-color: {ItemBackgroundColor}; border: 1px solid {ItemBorderColor};";
}
```

### Border

Use border utilities to quickly style the border and border-radius of an element. Great for images, buttons, or any other element.

Please note that if your element doesn’t have any styles you will not be able to see any changes once you apply the . You still need to add your own CSS rules like  so that visually you can see the applied borders on an element.

```
<Span Border="Border.Is1">Border on all sides</Span>

<Span Border="Border.Is1.Rounded">Rounded</Span>

<Span Border="Border.Primary">Borders with primary color</Span>
```

### Overflow

Use overflow shorthand utilities for quickly configuring how content overflows an element.

This is an example of using  on an element with set width and height dimensions. By design, this content will vertically scroll.

This is an example of using  on an element with set width and height dimensions.

This is an example of using  on an element with set width and height dimensions.

This is an example of using  on an element with set width and height dimensions.

```
<Div Display="Display.Flex.Row.OnDesktop">
    <Div Overflow="Overflow.Auto" Padding="Padding.Is3" Margin="Margin.Is3.FromBottom.Is0.FromBottom.OnDesktop.Is3.FromEnd.OnDesktop" Background="Background.Light" Style="max-width: 260px; max-height: 100px;">
        This is an example of using <code>Overflow.Auto</code> on an element with set width and height dimensions. By design, this content will vertically scroll.
    </Div>
    <Div Overflow="Overflow.Hidden" Padding="Padding.Is3" Margin="Margin.Is3.FromBottom.Is0.FromBottom.OnDesktop.Is3.FromEnd.OnDesktop" Background="Background.Light" Style="max-width: 260px; max-height: 100px;">
        This is an example of using <code>Overflow.Hidden</code> on an element with set width and height dimensions.
    </Div>
    <Div Overflow="Overflow.Visible" Padding="Padding.Is3" Margin="Margin.Is3.FromBottom.Is0.FromBottom.OnDesktop.Is3.FromEnd.OnDesktop" Background="Background.Light" Style="max-width: 260px; max-height: 100px;">
        This is an example of using <code>Overflow.Visible</code> on an element with set width and height dimensions.
    </Div>
    <Div Overflow="Overflow.Scroll" Padding="Padding.Is3" Margin="Margin.Is3.FromBottom.Is0.FromBottom.OnDesktop.Is3.FromEnd.OnDesktop" Background="Background.Light" Style="max-width: 260px; max-height: 100px;">
        This is an example of using <code>Overflow.Scroll</code> on an element with set width and height dimensions.
    </Div>
</Div>
```

### Breakpoints by frameworks

| Blazorise   | Bootstrap   | Material   | Bulma      |
|-------------|-------------|------------|------------|
| Mobile      | xs          | xs         | mobile     |
| Tablet      | sm          | sm         | tablet     |
| Desktop     | md          | md         | desktop    |
| Widescreen  | lg          | lg         | widescreen |
| FullHD      | xl          | xl         | fullHD     |

###### On this page

#### 

## 