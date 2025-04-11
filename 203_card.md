# Blazorise Card component

Blazorise cards provide a flexible and extensible content container with multiple variants and options.

The &lt;Card&gt; component is a versatile component that can be used for anything from a panel to a static image. The card component has numerous helper components to make markup as easy as possible.

- &lt; Card&gt; the main container.
- &lt;Card&gt; the main container.
    - &lt;CardHeader&gt; optional header within a card.
    - &lt;CardImage&gt; optional image within a card.
    - &lt; CardBody&gt; The building block of a card.
    - &lt;CardBody&gt; The building block of a card.
        - &lt;CardTitle&gt; required title within a card.
        - &lt;CardSubtitle&gt; optional subtitle within a card.
        - &lt;CardText&gt; optional text within a card.
    - &lt;CardFooter&gt; optional footer within a card.
- &lt;CardGroup&gt; groups cards together.
- &lt;CardDeck&gt; groups cards together with equal width and height.

### Default card

Use the following simple card component with a title and description.

### Card title

This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.

```
<Card>
    <CardBody>
        <CardTitle Size="3">
            Card title
        </CardTitle>
        <CardText>
            This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.
        </CardText>
    </CardBody>
</Card>
```

### Card with button

Use the following example of a card element if you also want to have an action button.

### Card title

This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.

```
<Card>
    <CardBody>
        <CardTitle Size="3">
            Card title
        </CardTitle>
        <CardText>
            This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.
        </CardText>
        <Button Color="Color.Primary" Margin="Margin.Is2.FromTop">
            Read more <Icon Name="IconName.ArrowRight" />
        </Button>
    </CardBody>
</Card>
```

### Card with image

You can use the following example of a card element with an image for blog posts, user cards, and many more.

<!-- image -->

### Card title

This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.

```
<Card>
    <CardImage Source="/img/gallery/2.jpg" Alt="Placeholder image" />
    <CardBody>
        <CardTitle Size="3">
            Card title
        </CardTitle>
        <CardText>
            This is some text within a card body. Jelly lemon drops tiramisu chocolate cake cotton candy soufflé oat cake sweet roll. Sugar plum marzipan dragée topping cheesecake chocolate bar. Danish muffin icing donut.
        </CardText>
        <Button Color="Color.Primary" Margin="Margin.Is2.FromTop">
            Read more <Icon Name="IconName.ArrowRight" />
        </Button>
    </CardBody>
</Card>
```

### Card deck

A set of equal width and height cards that aren’t attached to one another.

<!-- image -->

##### Card title 1

This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.

<!-- image -->

##### Card title 2

This card has supporting text below as a natural lead-in to additional content.

<!-- image -->

##### Card title 3

This is a wider card with supporting text below as a natural lead-in to additional content. This card has even longer content than the first to show that equal height action.

```
<CardDeck>
    <Card>
        <CardImage Source="/img/gallery/2.jpg" Alt="Card image cap 3"></CardImage>
        <CardBody>
            <CardTitle Size="5">Card title 1</CardTitle>
            <CardText>
                This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.
            </CardText>
            <Button Color="Color.Primary">Button</Button>
        </CardBody>
    </Card>
    <Card>
        <CardImage Source="/img/gallery/3.jpg" Alt="Card image cap 9"></CardImage>
        <CardBody>
            <CardTitle Size="5">Card title 2</CardTitle>
            <CardText>
                This card has supporting text below as a natural lead-in to additional content.
            </CardText>
            <Button Color="Color.Primary">Button</Button>
        </CardBody>
    </Card>
    <Card>
        <CardImage Source="/img/gallery/4.jpg" Alt="Card image cap 12"></CardImage>
        <CardBody>
            <CardTitle Size="5">Card title 3</CardTitle>
            <CardText>
                This is a wider card with supporting text below as a natural lead-in to additional content. This card has even longer content than the first to show that equal height action.
            </CardText>
            <Button Color="Color.Primary">Button</Button>
        </CardBody>
    </Card>
</CardDeck>
```

### Background color

If you want to make the card standout you can set its background color.

Please note, depending on the used background color you might need to adjust the text color. This can be done by setting the WhiteText parameters.

### Card title

With supporting text below as a natural lead-in to additional content.

```
<Card Background="Background.Success" WhiteText>
    <CardBody>
        <CardTitle Size="3">
            Card title
        </CardTitle>
        <CardText>
            With supporting text below as a natural lead-in to additional content.
        </CardText>
        <Button Color="Color.Primary" Margin="Margin.Is2.FromTop">
            Read more <Icon Name="IconName.ArrowRight" />
        </Button>
    </CardBody>
</Card>
```

## API

### Parameters

#### Card

| Parameter    | Description                                            | Type           | Default   |
|--------------|--------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this Card. | RenderFragment | null      |
| WhiteText    | Sets the white text when using the darker background.  | bool           | false     |

#### CardText

| Parameter       | Description                                                                       | Type           | Default   |
|-----------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                       | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event. | bool           | false     |
| Italic          | Italicize text if set to true.                                                    | bool           | false     |

#### CardTitle

| Parameter       | Description                                                                                                            | Type           | Default   |
|-----------------|------------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                                                            | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event.                                      | bool           | false     |
| Italic          | Italicize text if set to true.                                                                                         | bool           | false     |
| Size            | Number from 1 to 6 that defines the title size where the smaller number means larger text.Remarks TODO: change to enum | int?           | null      |

#### CardSubtitle

| Parameter       | Description                                                                                                               | Type           | Default   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this component.                                                               | RenderFragment | null      |
| CopyToClipboard | If true, the content of the component will be copied to clipboard on click event.                                         | bool           | false     |
| Italic          | Italicize text if set to true.                                                                                            | bool           | false     |
| Size            | Number from 1 to 6 that defines the subtitle size where the smaller number means larger text.Remarks todo: change to enum | int            | 6         |

#### CardLink

| Parameter    | Description                                                                  | Type           | Default        |
|--------------|------------------------------------------------------------------------------|----------------|----------------|
| Alt          | Alternative link text.                                                       | string         |                |
| ChildContent | Specifies the content to be rendered inside this Link.                       | RenderFragment | null           |
| Disabled     | Makes the link look inactive by adding the disabled boolean attribute.       | bool           | false          |
| Match        | URL matching behavior for a link.Possible values:Prefix, All, Custom         | Match          | Match.Prefix   |
| Source       | Link url.                                                                    | string         |                |
| Stretched    | Makes any HTML element or component clickable by “stretching” a nested link. | bool           | false          |
| Target       | The target attribute specifies where to open the linked document.            | Target         | Target.Default |
| Title        | Specify extra information about the element.                                 | string         |                |
| To           | Denotes the target route of the link.                                        | string         |                |
| Unstyled     | Removes default color styles from the link.                                  | bool           | false          |

#### CardImage

| Parameter    | Description                                                 | Type           | Default   |
|--------------|-------------------------------------------------------------|----------------|-----------|
| Alt          | Alternative image text.                                     | string         |           |
| ChildContent | Specifies the content to be rendered inside this CardImage. | RenderFragment | null      |
| Source       | Image url.                                                  | string         |           |

### Events

#### CardLink

| Event       | Description                                                                                                                                  | Type                          |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| Clicked     | Occurs when the link is clicked.                                                                                                             | EventCallback<MouseEventArgs> |
| CustomMatch | A callback function that is used to compare current uri with the user defined uri. If defined, the CardLink.Match parameter will be ignored. | Func<string, bool>            |

###### On this page

#### 

## 