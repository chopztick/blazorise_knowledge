# Blazorise Image component

A powerful tool for displaying images on the web.

The Blazorise &lt;Image&gt; component is a flexible and customizable component that can be used to display various types of images, including local images and remote images from external sources. The component allows you to set various attributes such as the image source, alt text, width, and height, and also provides a number of CSS classes to customize the appearance of the image.

One of the key features of the Blazorise image component is its ability to handle different image formats, including JPEG, PNG, SVG, and GIF. Additionally, the component supports lazy loading of images, which improves the performance of the web page by loading images only when they are needed.

## Examples

### Basic example

Simply set the  attribute and you’re good to go.

<!-- image -->

```
<Image Source="_content/Blazorise.Docs/assets/img/animals/animal-01.jpg" Text="A lovely animal..." />
```

### Deferred Loading

Add  parameter to enable image to dynamically load when you scroll into view.

<!-- image -->

```
<Image Source="_content/Blazorise.Docs/assets/img/animals/animal-06.jpg" Text="A lovely animal..." Loading />
```

### Fluid image

By enabling  parameter, it forces an image to take up the whole width of its container.

<!-- image -->

```
<Image Source="_content/Blazorise.Docs/assets/img/animals/animal-02-large.jpg" Text="A lovely animal..." Fluid />
```

### SEO friendly

The parameter Text gives alternate (alt) text for an image, which is good for SEO optimizations.

If you inspect the image with devtools you will be able to see alt assigned.

<!-- image -->

```
<Image Source="_content/Blazorise.Docs/assets/img/animals/animal-05.jpg" Text="A lovely animal..." />
```

## API

### Parameters

| Parameter   | Description                                                                         | Type   | Default   |
|-------------|-------------------------------------------------------------------------------------|--------|-----------|
| Fluid       | Forces an image to take up the whole width.                                         | bool   | false     |
| Loading     | Deffers loading the image until it reaches a calculated distance from the viewport. | bool   | false     |
| Source      | The absolute or relative URL of the image.                                          | string |           |
| Text        | Alternate text for an image.                                                        | string |           |

###### On this page

#### 

## 