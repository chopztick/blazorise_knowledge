# Blazorise Link component

Provides declarative, accessible navigation around your application.

The &lt;Link&gt; component allows you to easily customize anchor elements with your theme colors and typography styles.
    Link is the building block for most Blazorise components that offer link functionality. A Link component behaves
    like an &lt;a&gt; element, except it toggles an active CSS class based on whether its href matches the
    current URL.

due to a 
        in VisualStudio tooling you should write  as  until the issue is resolved.
        Or if you prefer the alternative, you can also use the  alias.

## Examples

### Basic

By specifying a value in the  property, a standard link () element will be rendered.

```
<Link To="docs">
    Link
</Link>
```

### Anchor Links

A  in front of a link location specifies that the link is pointing to an anchor on a page.
        (Anchor meaning a specific place in the middle of your page).

        Typically  will cause the document to scroll to the top of page when clicked.
         addresses this by preventing the default action (scroll to top) when  is set to .
        If you need scroll to top behavior, use a standard  tag.

```
<Link To="#b-docs-page-title">
    Link
</Link>
```

### Target

If you want to open link in a new tab or window you can use the  parameter.

```
<Link To="https://github.com/Megabit/Blazorise" Target="Target.Blank">
    Blazorise
</Link>
```

### Target iframe

By assigning a name to a frame via the name attribute, you can refer to it as the "target" of links defined by other elements. Our  parameter can also accept string values.

```
<Link To="some-url" Target="@("example")">
    This link can lead to iframe
</Link>

<iframe name="example" src="init_fixed.html"></iframe>
```

### Stretched link

Add Stretched attribute to a link to make its containing block clickable via a ::after pseudo element. In most cases, this means that an element with position: relative that contains a link with the stretched link class is clickable. Please note given how CSS position works, stretched-link cannot be mixed with most table elements.

Cards have position: relative by default, so in this case you can safely add the Stretched attribute to a link in the card without any other HTML changes.

<!-- image -->

### Card with stretched link

Some quick example text to build on the card title and make up the bulk of the card's content.

```
<Card Width="Width.Rem(18)">
    <CardImage Source="/img/gallery/2.jpg" Alt="Placeholder image" />
    <CardBody>
        <CardTitle Size="3">
            Card with stretched link
        </CardTitle>
        <CardText>
            Some quick example text to build on the card title and make up the bulk of the card's content.
        </CardText>
        <Link To="#" Title="Link to go somewhere" Stretched>
            Go somewhere
        </Link>
    </CardBody>
</Card>
```

### Disabled link

Make links look inactive by adding the Disabled boolean attribute to any &lt;Link&gt; element.

The disabled class uses pointer-events: none to try to disable the link functionality of &lt;a&gt;s, but that CSS property is not yet standardized. In addition, even in browsers that do support pointer-events: none, keyboard navigation remains unaffected, meaning that sighted keyboard users and users of assistive technologies will still be able to activate these links. So to be safe, add a tabindex="-1" attribute on these links (to prevent them from receiving keyboard focus) and use custom JavaScript to disable their functionality.

This is an example of a disabled link.

```
<Paragraph>
    This is an example of a <Link To="#" Disabled>disabled link</Link>.
</Paragraph>
```

## API

### Parameters

| Parameter    | Description                                                                  | Type           | Default        |
|--------------|------------------------------------------------------------------------------|----------------|----------------|
| ChildContent | Specifies the content to be rendered inside this Link.                       | RenderFragment | null           |
| Disabled     | Makes the link look inactive by adding the disabled boolean attribute.       | bool           | false          |
| Match        | URL matching behavior for a link.Possible values:Prefix, All, Custom         | Match          | Match.Prefix   |
| Stretched    | Makes any HTML element or component clickable by “stretching” a nested link. | bool           | false          |
| Target       | The target attribute specifies where to open the linked document.            | Target         | Target.Default |
| Title        | Specify extra information about the element.                                 | string         |                |
| To           | Denotes the target route of the link.                                        | string         |                |
| Unstyled     | Removes default color styles from the link.                                  | bool           | false          |

### Events

| Event       | Description                                                                                                                              | Type                          |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| Clicked     | Occurs when the link is clicked.                                                                                                         | EventCallback<MouseEventArgs> |
| CustomMatch | A callback function that is used to compare current uri with the user defined uri. If defined, the Link.Match parameter will be ignored. | Func<string, bool>            |

###### On this page

#### 

## 