# Blazorise Animate component

Animate your content by wrapping it with the Animate component.

The Animate component provides a wrapper that will animate your content. It is based on the AOS javascript library.

Blazorise acts as a wrapper for the animation functionality provided by the aos library. If you're having any issues please make sure to also take a look at the aos library repository.

There might be certain content, that due to how they are structured/styled might not be possible to animate.

It is not possible to animate:

- Modal

Take note, that certain elements in the page may affect how the aos library finds the "offset" element necessary to trigger the animation. It is known that Sidebars for instance can affect this behaviour.
        To make sure your content is successfully animated you may configure the  parameter giving the  component the necessary information to work.

        For example, the animate example given below, is configured as explained.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Animate
```

### Imports

In your main  add:

```
@using Blazorise.Animate
```

### Static Files

Add  to your  or  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<script src="_content/Blazorise.Animate/blazorise.animate.js?v=1.7.5.0"></script>
```

### Example

```
<Field>
    <Select TValue="string" SelectedValueChanged="@OnSelectedAnimationChanged">
        @foreach ( var availableAnimation in Animations.GetNames() )
        {
            <SelectItem Value="@availableAnimation">@availableAnimation</SelectItem>
        }
    </Select>
</Field>

@if ( showAnimate )
{
    <Div ElementId="#b-animate">
        <Animate Anchor="#b-animate" Auto Animation="selectedAnimation" DelayMilliseconds="500">
            <Card Margin="Margin.Is4.OnY">
                <CardBody>
                    <CardTitle Size="5">Animation Example</CardTitle>
                    <CardText>
                        Some content.
                    </CardText>
                </CardBody>
            </Card>
        </Animate>
    </Div>
}
<Button Color="Color.Primary" Clicked="@Animate">
    @buttonText
</Button>
```

```
@code {
    private IAnimation selectedAnimation = Animations.FadeIn;
    private bool showAnimate = false;
    private string buttonText = "Animate!";

    private Task OnSelectedAnimationChanged( string selectedAnimationName )
    {
        showAnimate = false;

        if ( Animations.TryParse( selectedAnimationName, out var animation ) )
            selectedAnimation = animation;
        else
            selectedAnimation = null;

        return Task.CompletedTask;
    }

    private async Task Animate()
    {
        if ( !showAnimate )
        {
            showAnimate = true;
            await InvokeAsync( StateHasChanged );
            buttonText = "Restart!";
        }
        else
        {
            showAnimate = false;
            buttonText = "Animate!";
        }

        await InvokeAsync( StateHasChanged );
    }
}
```

## API

### Parameters

| Parameter            | Description                                                                                                                                      | Type                       | Default                                          |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|--------------------------------------------------|
| Anchor               | Element whose offset will be used to trigger animation instead of an actual one.                                                                 | string                     |                                                  |
| AnchorPlacement      | Defines which position of the element regarding to window should trigger the animation.                                                          | string                     |                                                  |
| Animation            | Gets or sets the animation effect.Remarks The list of all supported animations can be found in Animate.Animations class.                         | IAnimation                 | null                                             |
| Attributes           | Captures all the custom attribute that are not part of Animate.Animate component.                                                                | Dictionary<string, object> | null                                             |
| Auto                 | True if the animation will be executed automatically. Otherwise if false it needs to      be run manually with Animate.Animate.Run method.       | bool                       | true                                             |
| ChildContent         | Specifies the content to be rendered inside this Animate.Animate.                                                                                | RenderFragment             | null                                             |
| Delay                | Gets os sets the delay of the animation before it runs automatically, or manually.Remarks Values from 0 to 3000, with step 50ms.                 | TimeSpan?                  | null                                             |
| DelayMilliseconds    | Gets os sets the delay in milliseconds of the animation before it runs automatically, or manually.Remarks Values from 0 to 3000, with step 50ms. | int?                       | null                                             |
| Duration             | Gets os sets the total duration of the animation.Remarks Values from 0 to 3000, with step 50ms.                                                  | TimeSpan?                  | null                                             |
| DurationMilliseconds | Gets os sets the total duration of the animation, in milliseconds.Remarks Values from 0 to 3000, with step 50ms.                                 | int?                       | null                                             |
| Easing               | Gets or sets the easing effect.Remarks The list of all supported easings can be found in Animate.Easings class.                                  | IEasing                    | null                                             |
| ElementId            | Gets or sets the animate element id.                                                                                                             | string                     |                                                  |
| Mirror               | Whether elements should animate out while scrolling past them.                                                                                   | bool?                      | null                                             |
| Offset               | Shifts the trigger point of the animation.                                                                                                       | int                        | 0                                                |
| Once                 | Whether animation should happen only once - while scrolling down.                                                                                | bool?                      | null                                             |
| Options              | Defines the animate options.                                                                                                                     | AnimateOptions             | null                                             |
| OptionsName          | Defines the custom name of the options to get from the configuration.                                                                            | string                     | Microsoft.Extensions.Options.Options.DefaultName |

### Methods

| Method   | Description                  | Return   | Parameters   |
|----------|------------------------------|----------|--------------|
| Run      | Runs the animation manually. | void     |              |

###### On this page

#### 

## 