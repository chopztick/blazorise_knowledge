# Blazorise CSS Grid Utilities

Quickly manage the layout, alignment, and sizing of grid columns, navigation, components, and more with a full suite of responsive grid utilities.

## Overview

With Blazorise, we’ve added the option to enable a separate grid system that’s built on CSS Grid, but with a Blazorise twist.

## Examples

### Three columns

Three equal-width columns across all viewports and devices can be created by using the GridColumns.Are3 utilities.

Col 4

Col 4

Col 4

```
<Grid Columns="GridColumns.Are3">
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        Col 4
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        Col 4
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        Col 4
    </Alert>
</Grid>
```

### Wrapping

Grid items automatically wrap to the next line when there’s no more room horizontally. Note that the gap applies to horizontal and vertical gaps between grid items.

Col 6

Col 6

Col 6

Col 6

```
<Grid>
    <Column ColumnSize="ColumnSize.Is6">
        <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
            Col 6
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is6">
        <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
            Col 6
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is6">
        <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
            Col 6
        </Alert>
    </Column>
    <Column ColumnSize="ColumnSize.Is6">
        <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
            Col 6
        </Alert>
    </Column>
</Grid>
```

### Auto columns

When there are no classes on the grid items (the immediate children of a Grid), each grid item will automatically be sized to one column.

1

1

1

1

1

1

1

1

1

1

1

1

```
<Grid>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
</Grid>
```

This behavior can be mixed with grid column classes.

Col 6

1

1

1

1

1

1

```
<Grid>
    <Column ColumnSize="ColumnSize.Is6">
        <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
            Col 6
        </Alert>
    </Column>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
    <Alert Color="Color.Primary" Visible Margin="Margin.Is0">
        1
    </Alert>
</Grid>
```

## API

### Attributes

#### Grid

| Name    | Description                                      | Type               | Default   |
|---------|--------------------------------------------------|--------------------|-----------|
| Rows    | Defines the number of rows to show in a grid.    | IFluentGridRows    | null      |
| Columns | Defines the number of columns to show in a grid. | IFluentGridColumns | null      |

###### On this page

#### 

## 