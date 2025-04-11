# Blazorise Table component

Basic table is just for data display.

Table displays information in a way that's easy to scan, so that users can look for patterns and insights. They can be embedded in primary content, such as cards.

- &lt; Table&gt; the main container.
- &lt;Table&gt; the main container.
    - &lt; TableHeader&gt; the optional top part of the table.
    - &lt;TableHeader&gt; the optional top part of the table.
        - &lt; TableRow&gt; header row .
        - &lt;TableRow&gt; header row.
            - &lt;TableHeaderCell&gt; a header cell.
    - &lt;TableFooter&gt; the optional bottom part of the table.
    - &lt; TableBody&gt; the main content of the table.
    - &lt;TableBody&gt; the main content of the table.
        - &lt; TableRow&gt; each table row .
        - &lt;TableRow&gt; each table row.
            - &lt;TableRowHeader&gt; a table cell heading.
            - &lt;TableRowCell&gt; a table cell.

## Examples

### Simple

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Striped

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Striped>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Hoverable

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Hoverable>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Bordered

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Bordered>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Borderless

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Borderless>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Small table

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Narrow>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Light header

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table>
    <TableHeader ThemeContrast="ThemeContrast.Light">
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Dark header

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table>
    <TableHeader ThemeContrast="ThemeContrast.Dark">
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Mobile Mode

In this mode the table may have limited functionality.

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table ResponsiveMode="TableResponsiveMode.Mobile">
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader MobileModeCaption="#">1</TableRowHeader>
            <TableRowCell MobileModeCaption="First Name">Mark</TableRowCell>
            <TableRowCell MobileModeCaption="Last Name">Otto</TableRowCell>
            <TableRowCell MobileModeCaption="Username">@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader MobileModeCaption="#">2</TableRowHeader>
            <TableRowCell MobileModeCaption="First Name">Jacob</TableRowCell>
            <TableRowCell MobileModeCaption="Last Name">Thornton</TableRowCell>
            <TableRowCell MobileModeCaption="Username">@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader MobileModeCaption="#">3</TableRowHeader>
            <TableRowCell MobileModeCaption="First Name">Larry</TableRowCell>
            <TableRowCell MobileModeCaption="Last Name">the Bird</TableRowCell>
            <TableRowCell MobileModeCaption="Username">@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Fixed header

|   # | First Name     | Last Name      | Username       |
|-----|----------------|----------------|----------------|
|   1 | Column content | Column content | Column content |
|   2 | Column content | Column content | Column content |
|   3 | Column content | Column content | Column content |
|   4 | Column content | Column content | Column content |
|   5 | Column content | Column content | Column content |
|   6 | Column content | Column content | Column content |
|   7 | Column content | Column content | Column content |
|   8 | Column content | Column content | Column content |
|   9 | Column content | Column content | Column content |
|  10 | Column content | Column content | Column content |

```
<Table FixedHeader FixedHeaderTableHeight="300px">
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        @for ( int i = 1; i <= 10; ++i )
        {
            var index = i.ToString();

            <TableRow @key="@index">
                <TableRowHeader>@index</TableRowHeader>
                <TableRowCell>Column content</TableRowCell>
                <TableRowCell>Column content</TableRowCell>
                <TableRowCell>Column content</TableRowCell>
            </TableRow>
        }
    </TableBody>
</Table>
```

### Fixed columns

Implementing this feature involves setting the  attribute to  for anchoring to the left, or  for anchoring to the right, on a cell. Additionally, you must enable fixed columns on a table with the  attribute.

|   # | Column 1   | Fixed heading   | Column 2   | Column 3   | Column 4   | Fixed end heading   | Fixed end heading   |
|-----|------------|-----------------|------------|------------|------------|---------------------|---------------------|
|   1 | Column 1   | Fixed column    | Column 2   | Column 3   | Column 4   | Fixed end content   | Fixed end content   |
|   2 | Column 1   | Fixed column    | Column 2   | Column 3   | Column 4   | Fixed end content   | Fixed end content   |
|   3 | Column 1   | Fixed column    | Column 2   | Column 3   | Column 4   | Fixed end content   | Fixed end content   |

```
<Table Bordered FixedColumns>
    <TableHeader>
        <TableRow>
            <TableHeaderCell Width="@Width.Px(50)" FixedPosition="TableColumnFixedPosition.Start">#</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(100)">Column 1</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(150)" FixedPosition="TableColumnFixedPosition.Start">Fixed heading</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(100)">Column 2</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(450)">Column 3</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(230)">Column 4</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(220)" FixedPosition="TableColumnFixedPosition.End">Fixed end heading</TableHeaderCell>
            <TableHeaderCell Width="@Width.Px(200)" FixedPosition="TableColumnFixedPosition.End">Fixed end heading</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        @for ( int i = 1; i <= 3; ++i )
        {
            var index = i.ToString();

            <TableRow @key="@index">
                <TableRowHeader Width="@Width.Px(50)" FixedPosition="TableColumnFixedPosition.Start">@index</TableRowHeader>
                <TableRowCell Width="@Width.Px(100)">Column 1</TableRowCell>
                <TableRowCell Width="@Width.Px(150)" FixedPosition="TableColumnFixedPosition.Start">Fixed column</TableRowCell>
                <TableRowCell Width="@Width.Px(200)">Column 2</TableRowCell>
                <TableRowCell Width="@Width.Px(450)">Column 3</TableRowCell>
                <TableRowCell Width="@Width.Px(230)">Column 4</TableRowCell>
                <TableRowCell Width="@Width.Px(220)" FixedPosition="TableColumnFixedPosition.End">Fixed end content</TableRowCell>
                <TableRowCell Width="@Width.Px(200)" FixedPosition="TableColumnFixedPosition.End">Fixed end content</TableRowCell>
            </TableRow>
        }
    </TableBody>
</Table>
```

### Scroll To a Row Or Pixel Offset

|   # | First Name     | Last Name      | Username       |
|-----|----------------|----------------|----------------|
|   1 | Column content | Column content | Column content |
|   2 | Column content | Column content | Column content |
|   3 | Column content | Column content | Column content |
|   4 | Column content | Column content | Column content |
|   5 | Column content | Column content | Column content |
|   6 | Column content | Column content | Column content |
|   7 | Column content | Column content | Column content |
|   8 | Column content | Column content | Column content |
|   9 | Column content | Column content | Column content |
|  10 | Column content | Column content | Column content |

```
<Button Size="Size.Small" Color="Color.Primary" Clicked="@ScrollToRow">Scroll To Row</Button>
<Button Size="Size.Small" Color="Color.Primary" Clicked="@ScrollToPixels">Scroll To Pixels</Button>

<Table @ref="@tableRef" FixedHeader FixedHeaderTableHeight="300px">
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        @for ( int i = 1; i <= 10; ++i )
        {
            var index = i.ToString();

            <TableRow @key="@index">
                <TableRowHeader>@index</TableRowHeader>
                <TableRowCell>Column content</TableRowCell>
                <TableRowCell>Column content</TableRowCell>
                <TableRowCell>Column content</TableRowCell>
            </TableRow>
        }
    </TableBody>
</Table>
```

```
@code {
    Table tableRef;

    private Task ScrollToRow()
        => tableRef.ScrollToRow( 1 ).AsTask();

    private Task ScrollToPixels()
        => tableRef.ScrollToPixels( 250 ).AsTask();
}
```

### Resizable

The Resizable property of the Blazorise Table component determines whether the columns of the table can be resized by the user. When Resizable is set to true, the user can click and drag the edges of the column headers to adjust the width of the columns. When Resizable is set to false, the columns are fixed in size and cannot be resized by the user.

The ResizeMode property of the Table component in Blazorise can have two modes: Header and Columns.

Header: When ResizeMode is set to Header, the user can resize the columns by dragging the edges of the column headers. This means that the user can only adjust the width of the columns by interacting with the header row of the table.
                
Columns: When ResizeMode is set to Columns, the user can resize the columns by dragging the edges of the entire column, including the header and the body cells. This means that the user can adjust the width of the columns by interacting with any part of the column, not just the header.

To set the Resizable property of a Table component in Blazorise, you can use the following syntax:

|   # | First Name   | Last Name   | Username   |
|-----|--------------|-------------|------------|
|   1 | Mark         | Otto        | @mdo       |
|   2 | Jacob        | Thornton    | @fat       |
|   3 | Larry        | the Bird    | @twitter   |

```
<Table Bordered Resizable ResizeMode="TableResizeMode.Columns">
    <TableHeader>
        <TableRow>
            <TableHeaderCell>#</TableHeaderCell>
            <TableHeaderCell>First Name</TableHeaderCell>
            <TableHeaderCell>Last Name</TableHeaderCell>
            <TableHeaderCell>Username</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRow>
            <TableRowHeader>1</TableRowHeader>
            <TableRowCell>Mark</TableRowCell>
            <TableRowCell>Otto</TableRowCell>
            <TableRowCell>@@mdo</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>2</TableRowHeader>
            <TableRowCell>Jacob</TableRowCell>
            <TableRowCell>Thornton</TableRowCell>
            <TableRowCell>@@fat</TableRowCell>
        </TableRow>
        <TableRow>
            <TableRowHeader>3</TableRowHeader>
            <TableRowCell>Larry</TableRowCell>
            <TableRowCell>the Bird</TableRowCell>
            <TableRowCell>@@twitter</TableRowCell>
        </TableRow>
    </TableBody>
</Table>
```

### Grouping

To use the grouping feature in the Table component from Blazorise, you must manually define the groups using the TableRowGroup component. This component wraps the rows that belong to a specific group and allows you to customize the appearance and behavior of the group.

In this example, the Table component is grouped by the "Category" column, and the rows are organized into two groups: "Fruits" and "Vegetables". The TableRowGroup component specifies the value of the grouped column (e.g. "Fruits" or "Vegetables") and wraps the rows that belong to that group.

| Name       | Color      |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |            |
|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|------------|
| Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     | Fruits     |
| Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables | Vegetables |

```
<Table>
    <TableHeader>
        <TableRow>
            <TableHeaderCell>Name</TableHeaderCell>
            <TableHeaderCell>Color</TableHeaderCell>
        </TableRow>
    </TableHeader>
    <TableBody>
        <TableRowGroup Title="Fruits">
            <TableRow>
                <TableRowCell>Apple</TableRowCell>
                <TableRowCell>Red</TableRowCell>
            </TableRow>
            <TableRow>
                <TableRowCell>Banana</TableRowCell>
                <TableRowCell>Yellow</TableRowCell>
            </TableRow>
        </TableRowGroup>
        <TableRowGroup Title="Vegetables">
            <TableRow>
                <TableRowCell>Carrot</TableRowCell>
                <TableRowCell>Orange</TableRowCell>
            </TableRow>
            <TableRow>
                <TableRowCell>Pepper</TableRowCell>
                <TableRowCell>Green</TableRowCell>
            </TableRow>
        </TableRowGroup>
    </TableBody>
</Table>
```

## API

### Parameters

#### Table

| Parameter                 | Description                                                                                                                                                                                                                                                                    | Type                | Default                     |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|-----------------------------|
| Bordered                  | Adds borders to all the cells.                                                                                                                                                                                                                                                 | bool                | false                       |
| Borderless                | Makes the table without any borders.                                                                                                                                                                                                                                           | bool                | false                       |
| ChildContent              | Specifies the content to be rendered inside this Table.                                                                                                                                                                                                                        | RenderFragment      | null                        |
| ContextMenuPreventDefault | Used to prevent the default action for an Table.ContextMenu event.                                                                                                                                                                                                             | bool                | false                       |
| DragEndPreventDefault     | Used to prevent the default action for an Table.DragEnd event.                                                                                                                                                                                                                 | bool                | false                       |
| DragEnterPreventDefault   | Used to prevent the default action for an Table.DragEnter event.                                                                                                                                                                                                               | bool                | false                       |
| Draggable                 | Indicates whether the element can be dragged.                                                                                                                                                                                                                                  | bool                | false                       |
| DragLeavePreventDefault   | Used to prevent the default action for an Table.DragLeave event.                                                                                                                                                                                                               | bool                | false                       |
| DragOverPreventDefault    | Used to prevent the default action for an Table.DragOver event.                                                                                                                                                                                                                | bool                | false                       |
| DragPreventDefault        | Used to prevent the default action for an Table.Drag event.                                                                                                                                                                                                                    | bool                | false                       |
| DragStartPreventDefault   | Used to prevent the default action for an Table.DragStart event.                                                                                                                                                                                                               | bool                | false                       |
| DropPreventDefault        | Used to prevent the default action for an Table.Drop event.                                                                                                                                                                                                                    | bool                | false                       |
| FixedColumns              | Makes table have a fixed set of columns. This will make it so that the table columns could be fixed to the side of the table.                                                                                                                                                  | bool                | false                       |
| FixedColumnsPositionSync  | Gets or sets whether the Table.FixedColumns feature automatically resynchronizes the columns positions when they are added or removed.Remarks Enabling this feature may impact performance due to constant recalculations of fixed column positions.                           | bool                | false                       |
| FixedHeader               | Makes table have a fixed header and enables a scrollbar in the table body.                                                                                                                                                                                                     | bool                | false                       |
| FixedHeaderTableHeight    | Sets the table height when Table.FixedHeader feature is enabled (defaults to 300px).                                                                                                                                                                                           | string              | "300px"                     |
| FixedHeaderTableMaxHeight | Sets the table max height when Table.FixedHeader feature is enabled (defaults to 300px).                                                                                                                                                                                       | string              | "300px"                     |
| FullWidth                 | Makes the table to fill entire horizontal space.                                                                                                                                                                                                                               | bool                | true                        |
| Hoverable                 | Adds a hover effect when mousing over rows.                                                                                                                                                                                                                                    | bool                | false                       |
| Narrow                    | Makes the table more compact by cutting cell padding in half.                                                                                                                                                                                                                  | bool                | false                       |
| Resizable                 | Gets or sets whether users can resize Table's columns.                                                                                                                                                                                                                         | bool                | false                       |
| ResizeMode                | Gets or sets whether the user can resize on header or columns.Possible values:Header, Columns                                                                                                                                                                                  | TableResizeMode     | TableResizeMode.Header      |
| Responsive                | Makes table responsive by adding the horizontal scroll bar.Remarks In some cases Dropdown component placed inside of a table marked with Table.Responsive     flag might not show dropdown menu properly. To make it work you might need to add some     additional CSS rules. | bool                | false                       |
| ResponsiveMode            | Gets or sets the Table's responsive mode.Possible values:Default, Mobile                                                                                                                                                                                                       | TableResponsiveMode | TableResponsiveMode.Default |
| Striped                   | Adds stripes to the table.                                                                                                                                                                                                                                                     | bool                | false                       |

#### TableRowGroup

| Parameter                 | Description                                                                                                                                 | Type                | Default   |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------|-----------|
| ChildContent              | Specifies the content to be rendered inside this TableRow.                                                                                  | RenderFragment      | null      |
| ColumnSpan                | Determines the column span for the inner table cell.                                                                                        | int                 | 1000      |
| ContextMenuPreventDefault | Used to prevent the default action for an TableRowGroup.ContextMenu event.                                                                  | bool                | false     |
| DragEndPreventDefault     | Used to prevent the default action for an TableRowGroup.DragEnd event.                                                                      | bool                | false     |
| DragEnterPreventDefault   | Used to prevent the default action for an TableRowGroup.DragEnter event.                                                                    | bool                | false     |
| Draggable                 | Indicates whether the element can be dragged.                                                                                               | bool                | false     |
| DragLeavePreventDefault   | Used to prevent the default action for an TableRowGroup.DragLeave event.                                                                    | bool                | false     |
| DragOverPreventDefault    | Used to prevent the default action for an TableRowGroup.DragOver event.                                                                     | bool                | false     |
| DragPreventDefault        | Used to prevent the default action for an TableRowGroup.Drag event.                                                                         | bool                | false     |
| DragStartPreventDefault   | Used to prevent the default action for an TableRowGroup.DragStart event.                                                                    | bool                | false     |
| DropPreventDefault        | Used to prevent the default action for an TableRowGroup.Drop event.                                                                         | bool                | false     |
| Expanded                  | Defines if the group is expanded.                                                                                                           | bool                | false     |
| IndentTableCells          | Specifies a number of Table Cells to Indent on the Group Row.                                                                               | int                 | 0         |
| IndentTableCellTemplate   | Specifies the custom content inside an Indented Table Cell on the Group Row. A contextual index is provided according to the Indentation.   | RenderFragment<int> | null      |
| Title                     | Specifies the title to be rendered inside this TableRowGroup.                                                                               | string              |           |
| TitleTemplate             | Specifies the custom title content to be rendered inside this TableRowGroup. It has higher priority over the TableRowGroup.Title parameter. | RenderFragment      | null      |
| Toggleable                | Defines if the group TableRowGroup.Expanded property can be toggled by clicking. It is still possible to toggle it programatically.         | bool                | true      |

#### TableRowCell

| Parameter                 | Description                                                                                                | Type                     | Default                       |
|---------------------------|------------------------------------------------------------------------------------------------------------|--------------------------|-------------------------------|
| ChildContent              | Specifies the content to be rendered inside this TableRowCell.                                             | RenderFragment           | null                          |
| ClickPreventDefault       | Used to prevent the default action for an TableRowCell.OnClickHandler(MouseEventArgs) event.               | bool                     | false                         |
| ClickStopPropagation      | Used to stop progation of the click action event.                                                          | bool                     | false                         |
| Color                     | Gets or sets the cell variant color.                                                                       | Color                    | Color.Default                 |
| ColumnSpan                | Number of columns a cell should span.                                                                      | int?                     | null                          |
| ContextMenuPreventDefault | Used to prevent the default action for an TableRowCell.ContextMenu event.                                  | bool                     | false                         |
| DragEndPreventDefault     | Used to prevent the default action for an TableRowCell.DragEnd event.                                      | bool                     | false                         |
| DragEnterPreventDefault   | Used to prevent the default action for an TableRowCell.DragEnter event.                                    | bool                     | false                         |
| Draggable                 | Indicates whether the element can be dragged.                                                              | bool                     | false                         |
| DragLeavePreventDefault   | Used to prevent the default action for an TableRowCell.DragLeave event.                                    | bool                     | false                         |
| DragOverPreventDefault    | Used to prevent the default action for an TableRowCell.DragOver event.                                     | bool                     | false                         |
| DragPreventDefault        | Used to prevent the default action for an TableRowCell.Drag event.                                         | bool                     | false                         |
| DragStartPreventDefault   | Used to prevent the default action for an TableRowCell.DragStart event.                                    | bool                     | false                         |
| DropPreventDefault        | Used to prevent the default action for an TableRowCell.Drop event.                                         | bool                     | false                         |
| FixedPosition             | Defines the fixed position of the row cell within the table.Possible values:None, Start, End               | TableColumnFixedPosition | TableColumnFixedPosition.None |
| MobileModeCaption         | When the Table.ResponsiveMode is set to TableResponsiveMode.Mobile, this caption will be used for the row. | string                   |                               |
| RowSpan                   | Number of rows a cell should span.                                                                         | int?                     | null                          |

### Events

#### Table

| Event       | Description                                                                                                                               | Type                            |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| ContextMenu | The event is fired when an element or text selection is right clicked to show the context menu.                                           | EventCallback<BLMouseEventArgs> |
| Drag        | The drag event is fired every few hundred milliseconds as an element or text selection is being dragged by the user.                      | EventCallback<DragEventArgs>    |
| DragEnd     | The DragEnd event is fired when a drag operation is being ended (by releasing a mouse button or hitting the escape key).                  | EventCallback<DragEventArgs>    |
| DragEnter   | The DragEnter event is fired when a dragged element or text selection enters a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragLeave   | The DragLeave event is fired when a dragged element or text selection leaves a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragOver    | The DragOver event is fired when an element or text selection is being dragged over a valid drop target (every few hundred milliseconds). | EventCallback<DragEventArgs>    |
| DragStart   | The DragStart event is fired when the user starts dragging an element or text selection.                                                  | EventCallback<DragEventArgs>    |
| Drop        | The drop event is fired when an element or text selection is dropped on a valid drop target.                                              | EventCallback<DragEventArgs>    |

#### TableRowGroup

| Event           | Description                                                                                                                               | Type                            |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| Clicked         | Occurs when the row is clicked.                                                                                                           | EventCallback<MouseEventArgs>   |
| ContextMenu     | The event is fired when an element or text selection is right clicked to show the context menu.                                           | EventCallback<BLMouseEventArgs> |
| DoubleClicked   | Occurs when the row is double clicked.                                                                                                    | EventCallback<MouseEventArgs>   |
| Drag            | The drag event is fired every few hundred milliseconds as an element or text selection is being dragged by the user.                      | EventCallback<DragEventArgs>    |
| DragEnd         | The DragEnd event is fired when a drag operation is being ended (by releasing a mouse button or hitting the escape key).                  | EventCallback<DragEventArgs>    |
| DragEnter       | The DragEnter event is fired when a dragged element or text selection enters a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragLeave       | The DragLeave event is fired when a dragged element or text selection leaves a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragOver        | The DragOver event is fired when an element or text selection is being dragged over a valid drop target (every few hundred milliseconds). | EventCallback<DragEventArgs>    |
| DragStart       | The DragStart event is fired when the user starts dragging an element or text selection.                                                  | EventCallback<DragEventArgs>    |
| Drop            | The drop event is fired when an element or text selection is dropped on a valid drop target.                                              | EventCallback<DragEventArgs>    |
| ExpandedChanged | Defines if the group is expanded.                                                                                                         | EventCallback<bool>             |

#### TableRowCell

| Event       | Description                                                                                                                               | Type                            |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| Clicked     | Occurs when the row cell is clicked.                                                                                                      | EventCallback<BLMouseEventArgs> |
| ContextMenu | The event is fired when an element or text selection is right clicked to show the context menu.                                           | EventCallback<BLMouseEventArgs> |
| Drag        | The drag event is fired every few hundred milliseconds as an element or text selection is being dragged by the user.                      | EventCallback<DragEventArgs>    |
| DragEnd     | The DragEnd event is fired when a drag operation is being ended (by releasing a mouse button or hitting the escape key).                  | EventCallback<DragEventArgs>    |
| DragEnter   | The DragEnter event is fired when a dragged element or text selection enters a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragLeave   | The DragLeave event is fired when a dragged element or text selection leaves a valid drop target.                                         | EventCallback<DragEventArgs>    |
| DragOver    | The DragOver event is fired when an element or text selection is being dragged over a valid drop target (every few hundred milliseconds). | EventCallback<DragEventArgs>    |
| DragStart   | The DragStart event is fired when the user starts dragging an element or text selection.                                                  | EventCallback<DragEventArgs>    |
| Drop        | The drop event is fired when an element or text selection is dropped on a valid drop target.                                              | EventCallback<DragEventArgs>    |

### Methods

#### Table

| Method            | Description                                                                             | Return    | Parameters              |
|-------------------|-----------------------------------------------------------------------------------------|-----------|-------------------------|
| ScrollToPixels    | If table has Table.FixedHeader enabled, it will scroll position to the provided pixels. | ValueTask | int pixels              |
| ScrollToRow       | If table has Table.FixedHeader enabled, it will scroll position to the provided row.    | ValueTask | int row                 |
| OnDragHandler     | Event handler for BaseDraggableComponent.Drag event callback.                           | Task      | DragEventArgs eventArgs |
| OnDragOverHandler | Event handler for BaseDraggableComponent.DragOver event callback.                       | Task      | DragEventArgs eventArgs |

#### TableRowGroup

| Method            | Description                                                       | Return   | Parameters              |
|-------------------|-------------------------------------------------------------------|----------|-------------------------|
| OnDragHandler     | Event handler for BaseDraggableComponent.Drag event callback.     | Task     | DragEventArgs eventArgs |
| OnDragOverHandler | Event handler for BaseDraggableComponent.DragOver event callback. | Task     | DragEventArgs eventArgs |

#### TableRowCell

| Method            | Description                                                       | Return   | Parameters              |
|-------------------|-------------------------------------------------------------------|----------|-------------------------|
| OnDragHandler     | Event handler for BaseDraggableComponent.Drag event callback.     | Task     | DragEventArgs eventArgs |
| OnDragOverHandler | Event handler for BaseDraggableComponent.DragOver event callback. | Task     | DragEventArgs eventArgs |

###### On this page

#### 

## 