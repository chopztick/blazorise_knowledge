# Blazorise Divider component

Dividers are used to visually separate or group elements.

## Examples

### Basic

Dividers in their simplest form display a horizontal line.

I sit at my window this morning where the world like a passer-by stops for a moment, nods to me and goes.

There little thoughts are the rustle of leaves; they have their whisper of joy in my mind.

```
<Paragraph>
    I sit at my window this morning where the world like a passer-by stops for a moment, nods to me and goes.
</Paragraph>

<Divider />

<Paragraph>
    There little thoughts are the rustle of leaves; they have their whisper of joy in my mind.
</Paragraph>
```

### Dashed

Use  custom property to show divider with a dashes.

What language is thine, O sea?

The language of eternal question.

```
<Paragraph>
    What language is thine, O sea?
</Paragraph>

<Divider DividerType="DividerType.Dashed" />

<Paragraph>
    The language of eternal question.
</Paragraph>
```

### Dotted

Use  custom property to show divider with dots.

What language is thy answer, O sky?

The language of eternal silence.

```
<Paragraph>
    What language is thy answer, O sky?
</Paragraph>

<Divider DividerType="DividerType.Dotted" />

<Paragraph>
    The language of eternal silence.
</Paragraph>
```

### Text Content

Use  custom property to show text in the middle of a divider.

What a world of merriment their melody foretells !

How they tinkle, tinkle, tinkle, In the icy air of night !

```
<Paragraph>
    What a world of merriment their melody foretells !
</Paragraph>

<Divider DividerType="DividerType.TextContent" Text="Edgar Allan Poe" />

<Paragraph>
    How they tinkle, tinkle, tinkle, In the icy air of night !
</Paragraph>
```

## API

### Parameters

| Parameter   | Description                                                                                                | Type         | Default   |
|-------------|------------------------------------------------------------------------------------------------------------|--------------|-----------|
| DividerType | Defines the type and style of the divider.                                                                 | DividerType? | null      |
| Text        | Label that will appear between the solid lines when Divider.DividerType is set as DividerType.TextContent. | string       |           |

###### On this page

#### 

## 