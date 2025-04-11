# Blazorise Figure component

Documentation and examples for displaying related images and text with the figure component in Blazorise.

Anytime you need to display a piece of content—like an image with an optional caption, consider using a Figure.

## Structure

- &lt; Figure&gt; the main container.
- &lt;Figure&gt; the main container.
    - &lt;FigureImage&gt; source image to be displayed.
    - &lt;FigureCaption&gt; optional caption for the image.

## Examples

### Basic Example

Use the included ,  and  classes to provide some baseline styles for the HTML5  and  elements.

A caption for the above image.

<!-- image -->

```
<Figure Size="FigureSize.Is256x256">
    <FigureImage Source="img/empty-256x256.png" AlternateText="empty-256x256" />
    <FigureCaption>A caption for the above image.</FigureCaption>
</Figure>
```

### Rounded

Making the figure rounded is easy with the  attribute.

A caption for the above image.

<!-- image -->

```
<Figure Size="FigureSize.Is256x256">
    <FigureImage Source="img/empty-256x256.png" AlternateText="empty-256x256" Rounded />
    <FigureCaption>A caption for the above image.</FigureCaption>
</Figure>
```

## API

### Parameters

#### Figure

| Parameter    | Description                                                                                                                                 | Type           | Default             |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------|----------------|---------------------|
| ChildContent | Gets or sets the reference to the parent Figure component.                                                                                  | RenderFragment | null                |
| Size         | Gets or sets the figure size.Possible values:Default, Is16x16, Is24x24, Is32x32, Is48x48, Is64x64, Is96x96, Is128x128, Is256x256, Is512x512 | FigureSize     | default(FigureSize) |

#### FigureImage

| Parameter     | Description                                      | Type   | Default   |
|---------------|--------------------------------------------------|--------|-----------|
| AlternateText | Alternate text for an image.                     | string |           |
| Rounded       | True if container should have a rounded corners. | bool   | false     |
| Source        | The absolute or relative URL of the image.       | string |           |

###### On this page

#### 

## 