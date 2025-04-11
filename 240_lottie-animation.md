# Blazorise Lottie Animation Component

A LottieAnimation component used to embed JSON-based Lottie animations.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.LottieAnimation
```

### Imports

In your main  add:

```
@using Blazorise.LottieAnimation
```

## Examples

### Basic

To embed an animation you just need to define the  of the animation.

```
<LottieAnimation Path="https://assets2.lottiefiles.com/datafiles/WFKIUGAVvLl1azi/data.json" />
```

## Best Practices

### Fixed Height

While the animation will work fine without it, it is advised to define a fixed height, eg. &lt;LottieAnimation Style="height: 250px;"&gt;. That way, the user can see the loading animation until the component is fully loaded.

## API

### Parameters

| Parameter    | Description                                                                               | Type                     | Default                           |
|--------------|-------------------------------------------------------------------------------------------|--------------------------|-----------------------------------|
| CurrentFrame | Current playback frame                                                                    | double                   | 0                                 |
| Direction    | Animation playback directionPossible values:Forward, Backward                             | LottieAnimationDirection | default(LottieAnimationDirection) |
| Loop         | Whether or not the animation should loop, or a number of times the animation should loop. | LoopConfiguration        | true                              |
| Path         | Relative or absolute path to the animation object                                         | string                   |                                   |
| Paused       | Whether or not the animation is paused                                                    | bool                     | false                             |
| Renderer     | Renderer to usePossible values:Svg, Canvas, Html                                          | LottieAnimationRenderer  | LottieAnimationRenderer.Svg       |
| Speed        | Animation playback speed                                                                  | double                   | 1.0                               |

### Events

| Event               | Description                                                                                                                                                                                                                                      | Type                                          |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| Completed           | Called when the animation completes                                                                                                                                                                                                              | EventCallback                                 |
| CurrentFrameChanged | Called when the current frame changes           Warning: This event is triggered extremely frequently. Subscribing to this event can cause a significant increase      in the amount of messages sent over the websocket if using Blazor Server. | EventCallback<double>                         |
| Loaded              | Called when the animation finishes loading and the elements have been added to the DOM                                                                                                                                                           | EventCallback<LottieAnimationLoadedEventArgs> |
| LoopCompleted       | Called when a loop completes                                                                                                                                                                                                                     | EventCallback                                 |

### Methods

| Method                    | Description                                                                                                                 | Return   | Parameters                          |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------|----------|-------------------------------------|
| NotifyCompleted           | Notifies the lottie animation component that the animation has completed. Should not be called directly by the user!        | Task     |                                     |
| NotifyLoopCompleted       | Notifies the lottie animation component that an animation loop has completed. Should not be called directly by the user!    | Task     |                                     |
| NotifyLoaded              | Notifies the lottie animation component that the animation has finished loading. Should not be called directly by the user! | Task     | LottieAnimationLoadedEventArgs args |
| NotifyCurrentFrameChanged | Notifies the lottie animation component that the current frame has changed. Should not be called directly by the user!      | Task     | double currentFrame                 |

###### On this page

#### 

## 