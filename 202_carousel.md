# Blazorise Carousel component

Loop a series of images or texts in a limited space.

## Overview

The Carousel component in Blazorise is a versatile and dynamic user interface element that facilitates the display of sequential content. This could include images, text, or any other HTML elements arranged in individual CarouselSlide components. The Carousel seamlessly transitions from one slide to another, either through user interaction or automatically over time, providing an interactive and engaging method of content presentation. It's highly customizable, fitting various use cases from image galleries to text-based slideshows, making it a valuable component in any modern web application.

&lt;Carousel&gt; main container.
            
&lt;CarouselSlide&gt; individual slide content, such as images, text, or other HTML elements.

## Examples

### Basic

A basic example of a Blazorise  component includes multiple  components, each containing individual content. This Carousel displays one slide at a time, allowing users to navigate between the slides manually or automatically. Despite its simplicity, CarouselSlide components can house a variety of content, such as images, videos, or complex HTML structures.

```
<Carousel @bind-SelectedSlide="@selectedSlide">
    <CarouselSlide Name="1">
        <Image Source="img/gallery/1.jpg" Text="Lights image" Display="Display.Block" Width="Width.Is100" />
    </CarouselSlide>
    <CarouselSlide Name="2">
        <Image Source="img/gallery/2.jpg" Text="Keyboard image" Display="Display.Block" Width="Width.Is100" />
    </CarouselSlide>
    <CarouselSlide Name="3">
        <Image Source="img/gallery/3.jpg" Text="Road image" Display="Display.Block" Width="Width.Is100" />
    </CarouselSlide>
</Carousel>
```

```
@code{
    private string selectedSlide = "2";
}
```

## Best Practices

### Uniform Sizes

For optimal Carousel functionality in Blazorise, maintain uniform dimensions across all slides. Inconsistent sizes can cause disruptive resizing during transitions. This can be prevented by defining consistent widths and heights through additional CSS styles. Uniform slide dimensions provide a smoother user experience and a more visually appealing Carousel component.

## API

### Parameters

| Parameter               | Description                                                                                                               | Type                 | Default   |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------|----------------------|-----------|
| Autoplay                | Autoplays the carousel slides.                                                                                            | bool                 | false     |
| AutoRepeat              | Auto-repeats the carousel slides once they reach the end.                                                                 | bool                 | false     |
| ChildContent            | Specifies the content to be rendered inside this Carousel.                                                                | RenderFragment       | null      |
| Crossfade               | Animate slides with a fade transition instead of a slide.                                                                 | bool                 | false     |
| Interval                | Defines the interval (in milliseconds) after which the item will automatically slide.                                     | double               | 2000      |
| NextButtonLocalizer     | Function used to handle custom localization for next button that will override a default Localization.ITextLocalizer.     | TextLocalizerHandler | null      |
| PreviousButtonLocalizer | Function used to handle custom localization for previous button that will override a default Localization.ITextLocalizer. | TextLocalizerHandler | null      |
| SelectedSlide           | Gets or sets currently selected slide name.                                                                               | string               |           |
| ShowControls            | Specifies whether to show the controls that allows the user to navigate to the next or previous slide.                    | bool                 | true      |
| ShowIndicators          | Specifies whether to show an indicator for each slide.                                                                    | bool                 | true      |

### Events

| Event                | Description                                  | Type                  |
|----------------------|----------------------------------------------|-----------------------|
| SelectedSlideChanged | Occurs after the selected slide has changed. | EventCallback<string> |

### Methods

| Method         | Description                                                              | Return   | Parameters       |
|----------------|--------------------------------------------------------------------------|----------|------------------|
| SelectNext     | Selects the next slide in a sequence, relative to the current slide.     | Task     |                  |
| SelectPrevious | Selects the previous slide in a sequence, relative to the current slide. | Task     |                  |
| Select         | Selects the slide by its name.                                           | Task     | string name      |
| SlideIndex     | Gets the index of the slide with the specified name.                     | int      | string slideName |

###### On this page

#### 

## 