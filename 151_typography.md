# Blazorise Typography components

Control text size, alignment, wrapping, overflow, transforms and more.

We create a font convention to ensure the best presentation across different platforms.

## Examples

### Text

Displays a simple static text on a page.

```
<Text TextColor="TextColor.Primary">
    Lorem ipsum dolor sit amet.
</Text>
<Text TextColor="TextColor.Secondary">
    Cursus euismod quis viverra nibh cras.
</Text>
```

### Paragraph

Block of text separated from adjacent blocks by blank lines and/or first-line indentation.

Deliver great service experiences fast - without the complexity of traditional ITSM solutions.Accelerate critical development work and deploy.

Track work across the enterprise through an open, collaborative platform. Link issues across Jira and ingest data from other software development tools, so your IT support and operations teams have richer contextual information to rapidly respond to requests, incidents, and changes.

```
<Paragraph>
    Deliver great service experiences fast - without the complexity of traditional ITSM solutions.Accelerate critical development work and deploy.
</Paragraph>
<Paragraph>
    Track work across the enterprise through an open, collaborative platform. Link issues across Jira and ingest data from other software development tools, so your IT support and operations teams have richer contextual information to rapidly respond to requests, incidents, and changes.
</Paragraph>
```

### Lead

The leading text can be used as the first paragraph inside an article content page.

Deliver great service experiences fast - without the complexity of traditional ITSM solutions.Accelerate critical development work and deploy.

Track work across the enterprise through an open, collaborative platform. Link issues across Jira and ingest data from other software development tools, so your IT support and operations teams have richer contextual information to rapidly respond to requests, incidents, and changes.

```
<Lead>
    Deliver great service experiences fast - without the complexity of traditional ITSM solutions.Accelerate critical development work and deploy.
</Lead>
<Paragraph>
    Track work across the enterprise through an open, collaborative platform. Link issues across Jira and ingest data from other software development tools, so your IT support and operations teams have richer contextual information to rapidly respond to requests, incidents, and changes.
</Paragraph>
```

### Headings

All HTML headings,  through , are available.

h1. Blazorise heading

h2. Blazorise heading

h3. Blazorise heading

h4. Blazorise heading

h5. Blazorise heading

h6. Blazorise heading

```
<Heading Size="HeadingSize.Is1">h1. Blazorise heading</Heading>
<Heading Size="HeadingSize.Is2">h2. Blazorise heading</Heading>
<Heading Size="HeadingSize.Is3">h3. Blazorise heading</Heading>
<Heading Size="HeadingSize.Is4">h4. Blazorise heading</Heading>
<Heading Size="HeadingSize.Is5">h5. Blazorise heading</Heading>
<Heading Size="HeadingSize.Is6">h6. Blazorise heading</Heading>
```

### Display Headings

Traditional heading elements are designed to work best in the meat of your page content.
        When you need a heading to stand out, consider using a display heading—a larger, slightly more opinionated heading style.

Display 1

Display 2

Display 3

Display 4

```
<DisplayHeading Size="DisplayHeadingSize.Is1">Display 1</DisplayHeading>
<DisplayHeading Size="DisplayHeadingSize.Is2">Display 2</DisplayHeading>
<DisplayHeading Size="DisplayHeadingSize.Is3">Display 3</DisplayHeading>
<DisplayHeading Size="DisplayHeadingSize.Is4">Display 4</DisplayHeading>
```

### Unordered Lists

Use the  component to show an unordered or ordered list of items based on multiple styles, layouts, and variants.

#### Password requirements:

- At least 10 characters (and up to 100 characters)
- At least one lowercase character
- Inclusion of at least one special character, e.g., ! @ # ?

```
<Heading Size="HeadingSize.Is4">
    Password requirements:
</Heading>

<UnorderedList>
    <UnorderedListItem>
        At least 10 characters (and up to 100 characters)
    </UnorderedListItem>
    <UnorderedListItem>
        At least one lowercase character
    </UnorderedListItem>
    <UnorderedListItem>
        Inclusion of at least one special character, e.g., ! @@ # ?
    </UnorderedListItem>
</UnorderedList>
```

### Ordered Lists

Use the  component to show an ordered list of items based on multiple styles, layouts, and variants.

#### Top students:

1. Bonnie Green with 70 points
2. Jese Leos with 63 points
3. Leslie Livingston with 57 points

```
<Heading Size="HeadingSize.Is4">
    Top students:
</Heading>

<OrderedList>
    <OrderedListItem>
        <Strong>Bonnie Green</Strong> with <Strong>70</Strong> points
    </OrderedListItem>
    <OrderedListItem>
        <Strong>Jese Leos</Strong> with <Strong>63</Strong> points
    </OrderedListItem>
    <OrderedListItem>
        <Strong>Leslie Livingston</Strong> with <Strong>57</Strong> points
    </OrderedListItem>
</OrderedList>
```

### List Style Image

Control the marker image for list items using the ListStyleImage parameter.

This parameter accepts either a Base64 encoded string that represents an image, or a URL that points to an image resource.

- 5 cups chopped Porcini mushrooms
- 1/2 cup of olive oil
- 3lb of celery

```
<UnorderedList ListStyleImage="data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTIiIHZpZXdCb3g9IjAgMCAxNCAxMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiBmaWxsPSIjMzhiZGY4Ij48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik0xMy42ODUuMTUzYS43NTIuNzUyIDAgMCAxIC4xNDMgMS4wNTJsLTggMTAuNWEuNzUuNzUgMCAwIDEtMS4xMjcuMDc1bC00LjUtNC41YS43NS43NSAwIDAgMSAxLjA2LTEuMDZsMy44OTQgMy44OTMgNy40OC05LjgxN2EuNzUuNzUgMCAwIDEgMS4wNS0uMTQzWiIgLz48L3N2Zz4=">
    <UnorderedListItem>
        5 cups chopped Porcini mushrooms
    </UnorderedListItem>
    <UnorderedListItem>
        1/2 cup of olive oil
    </UnorderedListItem>
    <UnorderedListItem>
        3lb of celery
    </UnorderedListItem>
</UnorderedList>
```

### Unstyled List

Use the  parameter to disable the list style bullets or numbers.

#### Password requirements:

- At least 10 characters (and up to 100 characters)
- At least one lowercase character
- Inclusion of at least one special character, e.g., ! @ # ?

```
<Heading Size="HeadingSize.Is4">
    Password requirements:
</Heading>

<UnorderedList Unstyled>
    <UnorderedListItem>
        At least 10 characters (and up to 100 characters)
    </UnorderedListItem>
    <UnorderedListItem>
        At least one lowercase character
    </UnorderedListItem>
    <UnorderedListItem>
        Inclusion of at least one special character, e.g., ! @@ # ?
    </UnorderedListItem>
</UnorderedList>
```

### Text Size

The TextSize fluent utility in Blazorise provides an easy way to control the size of the text in your Blazor components. It comes with a range of predefined sizes and also supports heading sizes.

The usage of the TextSize fluent utility is quite straightforward. You just need to set the TextSize property of the Paragraph component (or any other component supporting this attribute) to one of the available enum values.

Also, as most of Blazorise fluent-based utilities, you can define different text sizes for different screens, eg. TextSize="TextSize.IsLarge.OnMobile.IsSmall.OnDesktop".

TextSize.ExtraSmall

TextSize.Small

TextSize.Default

TextSize.Medium

TextSize.Large

TextSize.ExtraLarge

TextSize.Heading1

TextSize.Heading2

TextSize.Heading3

TextSize.Heading4

TextSize.Heading5

TextSize.Heading6

```
<Row>
    <Column>
        <Paragraph TextSize="TextSize.ExtraSmall">
            TextSize.ExtraSmall
        </Paragraph>
        <Paragraph TextSize="TextSize.Small">
            TextSize.Small
        </Paragraph>
        <Paragraph TextSize="TextSize.Default">
            TextSize.Default
        </Paragraph>
        <Paragraph TextSize="TextSize.Medium">
            TextSize.Medium
        </Paragraph>
        <Paragraph TextSize="TextSize.Large">
            TextSize.Large
        </Paragraph>
        <Paragraph TextSize="TextSize.ExtraLarge">
            TextSize.ExtraLarge
        </Paragraph>
    </Column>
    <Column>
        <Paragraph TextSize="TextSize.Heading1">
            TextSize.Heading1
        </Paragraph>
        <Paragraph TextSize="TextSize.Heading2">
            TextSize.Heading2
        </Paragraph>
        <Paragraph TextSize="TextSize.Heading3">
            TextSize.Heading3
        </Paragraph>
        <Paragraph TextSize="TextSize.Heading4">
            TextSize.Heading4
        </Paragraph>
        <Paragraph TextSize="TextSize.Heading5">
            TextSize.Heading5
        </Paragraph>
        <Paragraph TextSize="TextSize.Heading6">
            TextSize.Heading6
        </Paragraph>
    </Column>
</Row>
```

### Text Decoration

Blazorise allows you to style text with various decorations. You can use underline to place a line beneath the text, line-through to strike through it, or overline to add a line above. To remove any decorations, use the none option. These styles help enhance and highlight text as needed.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog.

This link has its text decoration removed

```
<Row>
    <Column>
        <Paragraph TextDecoration="TextDecoration.Underline">
            The quick brown fox jumps over the lazy dog.
        </Paragraph>
        <Paragraph TextDecoration="TextDecoration.Overline">
            The quick brown fox jumps over the lazy dog.
        </Paragraph>
        <Paragraph TextDecoration="TextDecoration.LineThrough">
            The quick brown fox jumps over the lazy dog.
        </Paragraph>
        <Paragraph>
            <Anchor To="#" TextDecoration="TextDecoration.None">
                This link has its text decoration removed
            </Anchor>
        </Paragraph>
    </Column>
</Row>
```

## API

### Parameters

#### Text

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

#### Paragraph

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

#### Lead

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

#### Heading

| Parameter          | Description                                                                       | Type           | Default         |
|--------------------|-----------------------------------------------------------------------------------|----------------|-----------------|
| AlternativeTagName | Defines the alternative tag name for the heading element. Default is set to h1.   | string         |                 |
| ChildContent       | Specifies the content to be rendered inside this component.                       | RenderFragment | null            |
| CopyToClipboard    | If true, the content of the component will be copied to clipboard on click event. | bool           | false           |
| Italic             | Italicize text if set to true.                                                    | bool           | false           |
| Size               | Gets or sets the heading size.Possible values:Is1, Is2, Is3, Is4, Is5, Is6        | HeadingSize    | HeadingSize.Is3 |

#### DisplayHeading

| Parameter          | Description                                                                       | Type               | Default                |
|--------------------|-----------------------------------------------------------------------------------|--------------------|------------------------|
| AlternativeTagName | Defines the alternative tag name for the heading element. Default is set to h1.   | string             |                        |
| ChildContent       | Specifies the content to be rendered inside this component.                       | RenderFragment     | null                   |
| CopyToClipboard    | If true, the content of the component will be copied to clipboard on click event. | bool               | false                  |
| Italic             | Italicize text if set to true.                                                    | bool               | false                  |
| Size               | Gets or sets the display heading size.Possible values:Is1, Is2, Is3, Is4          | DisplayHeadingSize | DisplayHeadingSize.Is2 |

#### UnorderedList

| Parameter       | Description                                                                                                               | Type           | Default   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                                                               | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event.                                         | bool           | false     |
| Italic          | Italicize text if set to true.                                                                                            | bool           | false     |
| ListStyleImage  | Defines the marker images for list items. The paremeter accepts Base64 encoded string that represents an image, or a URL. | string         |           |
| Unstyled        | Remove the default list-style and left margin on list items (immediate children only).                                    | bool           | false     |

#### UnorderedListItem

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

#### OrderedList

| Parameter       | Description                                                                                              | Type            | Default                 |
|-----------------|----------------------------------------------------------------------------------------------------------|-----------------|-------------------------|
| ChildContent    | Specifies the content to be rendered inside this component.                                              | RenderFragment  | null                    |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event.                        | bool            | false                   |
| Italic          | Italicize text if set to true.                                                                           | bool            | false                   |
| ListStyleImage  | Defines the marker images for list items.                                                                | string          |                         |
| ListType        | Defines the type of item markers.Possible values:Default, LowerAlpha, LowerRoman, UpperAlpha, UpperRoman | OrderedListType | OrderedListType.Default |
| Unstyled        | Remove the default list-style and left margin on list items (immediate children only).                   | bool            | false                   |

#### OrderedListItem

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

###### On this page

#### 

## 