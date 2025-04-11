# Blazorise Splitter component

The Splitter component is a dynamic control element in Blazor that generates resizable split views in applications.

The Splitter component allows you to segment your application screen into adjustable, standalone sections, either horizontally or vertically. This flexible utility lends itself to a wide variety of applications, from visually dividing up workspace areas, managing multi-panel layouts, to providing adjustable content viewing areas. It’s designed to enhance usability and optimize screen real estate utilization, thereby improving overall user experience. The ease of integration with other Blazor components makes Splitter a versatile tool in building responsive, intuitive, and user-friendly interfaces.

## Installation

To get started with Blazorise.Splitter, follow these simple installation steps:

First, you need to add the Blazorise.Splitter package to your project. You can do this by running the following command in your project's root directory:

```
Install-Package Blazorise.Splitter
```

Alternatively, you can install the package using the .NET Core CLI:

```
dotnet add package Blazorise.Splitter
```

### Configuration

Once the package is installed, you need to configure your Blazor project to use the Splitter component.

In your main \_Imports.razor add:

```
@using Blazorise.Splitter
```

## Examples

When working with the Splitter component in Blazorise, it's essential to set the width or height appropriately based on the Direction mode of the splitter.

If the Direction mode is set to Horizontal, the splitter will create sections positioned side by side. In this mode, it's generally advisable to define the width of the Splitter component or its sections to ensure they render and behave as expected.

On the other hand, if the Direction mode is set to Vertical, the splitter will create sections stacked one on top of the other. In this case, defining the height for the Splitter component or its sections is recommended for proper rendering and functionality.

By setting these properties correctly according to the splitter direction, you can ensure a more predictable layout and a better user interaction experience.

### Horizontal Splitter

By default, the Splitter component creates a horizontal split. Here's a simple example:

Hello!

World!

```
<Splitter Style="height: 100px;">
    <SplitterSection>
        <div>Hello!</div>
    </SplitterSection>
    <SplitterSection>
        <div>World!</div>
    </SplitterSection>
</Splitter>
```

### Vertical Splitter

To create a vertical split, use the  parameter of the  component and set it to :

Hello!

World!

```
<Splitter Direction="SplitterDirection.Vertical" Style="height: 250px;">
    <SplitterSection>
        <div>Hello!</div>
    </SplitterSection>
    <SplitterSection>
        <div>World!</div>
    </SplitterSection>
</Splitter>
```

### Gutter Size

By adjusting the  value, you can control the thickness of the draggable area. A larger  makes the gutter wider and therefore easier to interact with, particularly on touch interfaces, while a smaller  makes the gutter more subtle.

Hello!

World!

```
<Splitter Style="height: 100px;" GutterSize="50">
    <SplitterSection>
        <div>Hello!</div>
    </SplitterSection>
    <SplitterSection>
        <div>World!</div>
    </SplitterSection>
</Splitter>
```

### Min Size

In this example, MinSize="50" would mean that this SplitterSection cannot be resized to less than 50 pixels.

This ensures that regardless of how much the user adjusts the split using the gutter, the section will not shrink below this minimum size. This can be very useful to ensure that content within each section remains readable and usable, regardless of the user's interactions.

Hello!

World!

```
<Splitter Style="height: 100px;">
    <SplitterSection MinSize="50">
        <div>Hello!</div>
    </SplitterSection>
    <SplitterSection>
        <div>World!</div>
    </SplitterSection>
</Splitter>
```

### Background Image

Using GutterBackgroundImage can help to enhance the visual appeal of your application, or provide additional context or functionality. For instance, a background image might be used to represent the direction of resizing, or simply to better match the overall design theme of your application.

This parameter accepts either a Base64 encoded string that represents an image, or a URL that points to an image resource.

Remember to choose an image that will look good when stretched or repeated across the width of the gutter, and that will not distract from the usability of the splitter.

Hello!

World!

```
<Splitter Style="height: 100px;" GutterSize="32" GutterBackgroundImage="_content/Blazorise.Docs/assets/img/icons/resize-horizontal-30.png">
    <SplitterSection>
        <div>Hello!</div>
    </SplitterSection>
    <SplitterSection>
        <div>World!</div>
    </SplitterSection>
</Splitter>
```

## API

### Parameters

#### Splitter

| Parameter             | Description                                                                                                                                                                                                                                        | Type                    | Default                        |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|--------------------------------|
| ChildContent          | Specifies the content to be rendered inside this Splitter.Splitter.                                                                                                                                                                                | RenderFragment          | null                           |
| Cursor                | Cursor to display while dragging.                                                                                                                                                                                                                  | string                  |                                |
| Direction             | Direction to split.Possible values:Horizontal, Vertical                                                                                                                                                                                            | SplitterDirection       | SplitterDirection.Horizontal   |
| DragInterval          | Drag this number of pixels at a time. Defaults to 1 for smooth dragging, but can be set to a pixel value to give more control over the resulting sizes.     Works particularly well when the Splitter.Splitter.GutterSize is set to the same size. | double                  | 1                              |
| ExpandToMin           | When the splitter is created, if ExpandToMin is true, the minSize for each element overrides the percentage value from the sizes option.                                                                                                           | bool?                   | null                           |
| GutterAlign           | Determines how the gutter aligns between the two elements.Possible values:Start, Center, End                                                                                                                                                       | SplitterGutterAlignment | SplitterGutterAlignment.Center |
| GutterBackgroundImage | Defines the custom background image for the gutter element.          This parameter accepts either a Base64 encoded string that represents an image, or a URL that points to an image resource.                                                    | string                  |                                |
| GutterSize            | Gutter size in pixels. Defaults to 10.                                                                                                                                                                                                             | double                  | 10                             |

#### SplitterSection

| Parameter    | Description                                                                | Type           | Default                 |
|--------------|----------------------------------------------------------------------------|----------------|-------------------------|
| ChildContent | Specifies the content to be rendered inside this Splitter.SplitterSection. | RenderFragment | null                    |
| MaxSize      | Maximum size of the section, specified as pixel value.                     | double         | double.PositiveInfinity |
| MinSize      | Minimum size of the section, specified as pixel value.                     | double         | 100                     |
| Size         | Initial size of a section element in percents or CSS values.               | double?        | null                    |
| SnapOffset   | Snap to minimum size offset in pixels.                                     | double         | 0                       |

###### On this page

#### 

## 