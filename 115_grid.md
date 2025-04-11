# Blazorise Grid Utilities

A simple way to build responsive columns with Flex grid system.

Blazorise comes with a 12 point grid system built using flexbox. The grid is used to create specific layouts within an application’s content. It contains 5 types of media breakpoints that are used for targeting specific screen sizes or orientations, xs, sm, md, lg and xl.

You might also be interested in out  utilities, which are based on a  system.

## Examples

### Rows &amp; Columns

As the grid can be divided into 12 columns, there are size classes for each division.
        These can be set using  followed by  -&gt; .

Is12

Is8

Is4

```
<Row>
    <Column ColumnSize="ColumnSize.Is12">
        <Alert Color="Color.Primary" Visible>
            Is12
        </Alert>
    </Column>
</Row>
<Row>
    <Column ColumnSize="ColumnSize.Is8">
        <Alert Color="Color.Primary" Visible>
            Is8
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is4">
        <Alert Color="Color.Secondary" Visible>
            Is4
        </Alert>
    </Column>
</Row>
```

### Offset

Move columns to the right using  attribute.

Is4

Is4.Is4.WithOffset

Is3.Is3.WithOffset

Is3.Is3.WithOffset

Is6.Is3.WithOffset

```
<Row>
    <Column ColumnSize="ColumnSize.Is4">
        <Alert Color="Color.Primary" Visible>
            Is4
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is4.Is4.WithOffset">
        <Alert Color="Color.Primary" Visible>
            Is4.Is4.WithOffset
        </Alert>
    </Column>
</Row>
<Row>
    <Column ColumnSize="ColumnSize.Is3.Is3.WithOffset">
        <Alert Color="Color.Primary" Visible>
            Is3.Is3.WithOffset
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is3.Is3.WithOffset">
        <Alert Color="Color.Primary" Visible>
            Is3.Is3.WithOffset
        </Alert>
    </Column>
</Row>
<Row>
    <Column ColumnSize="ColumnSize.Is6.Is3.WithOffset">
        <Alert Color="Color.Primary" Visible>
            Is6.Is3.WithOffset
        </Alert>
    </Column>
</Row>
```

### Gutter

Gutter can be used to set small spacing between Columns within a Row, without breaking the Grid wrapping rules (this is done by offsetting margins).

You can use it by setting the Gutter attribute on the Row. The Columns will automatically inherit this spacing and apply it.

Gutter is a tuple, which is (int Horizontal, int Vertical) based off pixel spacing.

In this example, each Column will get 16px of padding left and right, as well as 8px
            of padding top and bottom. The Row will offset the margin accordingly.

I have padding

I also have padding

```
<Row HorizontalGutter="32" VerticalGutter="16">
    <Column ColumnSize="ColumnSize.Is8">
        <Alert Color="Color.Primary" Visible>
            I have padding
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is4">
        <Alert Color="Color.Secondary" Visible>
            I also have padding
        </Alert>
    </Column>
</Row>
```

## Containers

Containers can be used as an easy and helpful way to display content with some default padding and margins for a clean UI.

### Container

This container will be centered on desktop.

Suspendisse vel quam malesuada, aliquet sem sit amet, fringilla elit. Morbi tempor tincidunt tempor. Etiam id turpis viverra, vulputate sapien nec, varius sem. Curabitur ullamcorper fringilla eleifend. In ut eros hendrerit est consequat posuere et at velit.

```
<Container>
    <Alert Color="Color.Primary" Visible>
        Suspendisse vel quam malesuada, aliquet sem sit amet, fringilla elit. Morbi tempor tincidunt tempor. Etiam id turpis viverra, vulputate sapien nec, varius sem. Curabitur ullamcorper fringilla eleifend. In ut eros hendrerit est consequat posuere et at velit.
    </Alert>
</Container>
```

### Fluid Container

If you don’t want to have a maximum width but want to keep the some margin on the left and right sides, add the  modifier:

Suspendisse vel quam malesuada, aliquet sem sit amet, fringilla elit. Morbi tempor tincidunt tempor. Etiam id turpis viverra, vulputate sapien nec, varius sem. Curabitur ullamcorper fringilla eleifend. In ut eros hendrerit est consequat posuere et at velit.

```
<Container Fluid>
    <Alert Color="Color.Primary" Visible>
        Suspendisse vel quam malesuada, aliquet sem sit amet, fringilla elit. Morbi tempor tincidunt tempor. Etiam id turpis viverra, vulputate sapien nec, varius sem. Curabitur ullamcorper fringilla eleifend. In ut eros hendrerit est consequat posuere et at velit.
    </Alert>
</Container>
```

### Responsive

Responsive containers allow you to specify a class that is 100% wide until the specified breakpoint is reached,
        after which we apply  for each of the higher breakpoints. For example, 
        is 100% wide to start until the  breakpoint is reached, where it will scale up
        with , , and .

100% wide until tablet breakpoint

100% wide until desktop breakpoint

100% wide until widescreen breakpoint

100% wide until full-hd breakpoint

```
<Container Breakpoint="Breakpoint.Tablet">
    <Alert Color="Color.Primary" Visible>
        100% wide until tablet breakpoint
    </Alert>
</Container>
<Container Breakpoint="Breakpoint.Desktop">
    <Alert Color="Color.Primary" Visible>
        100% wide until desktop breakpoint
    </Alert>
</Container>
<Container Breakpoint="Breakpoint.Widescreen">
    <Alert Color="Color.Primary" Visible>
        100% wide until widescreen breakpoint
    </Alert>
</Container>
<Container Breakpoint="Breakpoint.FullHD">
    <Alert Color="Color.Primary" Visible>
        100% wide until full-hd breakpoint
    </Alert>
</Container>
```

## API

### Attributes

#### Row

| Name   | Description                                                                                                        | Type       | Default   |
|--------|--------------------------------------------------------------------------------------------------------------------|------------|-----------|
| Gutter | Row grid spacing - we recommend setting Horizontal and/or Vertical it to (16 + 8n). (n stands for natural number.) | (int, int) | null      |

#### Column

| Name   | Description                                                                               | Type       | Default   |
|--------|-------------------------------------------------------------------------------------------|------------|-----------|
| Gutter | Column grid spacing, we recommend setting it to (16 + 8n). (n stands for natural number.) | (int, int) | null      |

#### Container

| Name       | Description                                                                               | Type       | Default   |
|------------|-------------------------------------------------------------------------------------------|------------|-----------|
| Breakpoint | Makes a full width container that is 100% wide until the specified breakpoint is reached. | Breakpoint | None      |
| Fluid      | Makes a full width container, spanning the entire width of the viewport.                  | bool       | false     |

###### On this page

#### 

## 