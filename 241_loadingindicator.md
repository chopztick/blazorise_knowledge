# Blazorise LoadingIndicator component

A wrapper component that adds a loading indicator to a child content. Default spinner courtesy of icons8.com.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.LoadingIndicator
```

### Imports

In your main  add:

```
@using Blazorise.LoadingIndicator
```

### Static files

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.LoadingIndicator/blazorise.loadingindicator.css" rel="stylesheet" />
```

### Basic example

The basic usage scenario for  with default settings using a  object reference.

```
<LoadingIndicator @ref="loadingIndicator">
    <LineChart TItem="double" Data="lineChartData" />
</LoadingIndicator>

<Button Clicked="UpdateChart" Color="Color.Primary">Update</Button>
```

```
@code 
{
    LoadingIndicator loadingIndicator;

    async Task UpdateChart()
    {
        await loadingIndicator.Show();

        await Task.Delay(3000); // Do work ...

        await loadingIndicator.Hide();
    }

    // sample data
    ChartData<double> lineChartData = new()
    {
        Labels = new() { "Jan", "Feb", "Mar", "Apr", "May", "Jun" },
        Datasets = new() { new LineChartDataset<double>()
        {
            Data = new List<double>() { 70, 90, 50, 60, 80, 100 },
        }}
    };
}
```

### Two-way Binding Example

Having a more declarative approach to control the indicator is also supported. To make it work, you just need to bind a variable to the  parameter, and it will work.

```
<LoadingIndicator @bind-Visible="@visible">
    <LineChart TItem="double" Data="lineChartData" />
</LoadingIndicator>

<Button Clicked="UpdateChart" Color="Color.Primary">Update</Button>
```

```
@code
{
    bool visible;

    async Task UpdateChart()
    {
        visible = true;

        await Task.Delay( 3000 ); // Do work ...

        visible = false;
    }

    // sample data
    ChartData<double> lineChartData = new()
    {
        Labels = new() { "Jan", "Feb", "Mar", "Apr", "May", "Jun" },
        Datasets = new() { new LineChartDataset<double>()
        {
            Data = new List<double>() { 70, 90, 50, 60, 80, 100 },
        }}
    };
}
```

### Application busy service

Use  to add a global application busy UI. Register  as a scoped service in your configuration.  automatically registers with  if one is registered or unless  property is set directly. Use dependency injection to obtain a reference to the  to control . The application busy UI comes with an awesome Blazorise logo spinner, which is recommended, but if you prefer the default spinner set  to .

Add  as a scoped service.

```
services.AddLoadingIndicator();
```

Add  to your  file.

```
<Router AppAssembly="typeof(App).Assembly">
	<Found>...</Found>
	<NotFound>...</NotFound>
</Router>

<ApplicationLoadingIndicator />
```

Inject  into your component where you want to trigger the application busy UI from.

```
@inject ILoadingIndicatorService ApplicationLoadingIndicatorService
```

```
@code 
{
    async Task DoWork()
    {
        await ApplicationLoadingIndicatorService.Show();
        
        // do work ...
        
        await ApplicationLoadingIndicatorService.Hide();
    }
}
```

### Using as cascading parameter

You can also use the wrapper as a cascading parameter.

To implement a global application busy UI using cascading parameter add the wrapper to your main layout.

```
<LoadingIndicator FullScreen>
    @Body
</LoadingIndicator>
```

Declare a  of type  in your component.

```
<Button Clicked="DoWork" />
```

```
@code
{
    [CascadingParameter]
    LoadingIndicator loadingIndicator;

    async Task DoWork()
    {
        await loadingIndicator.Show();
        
        // do work ...
        
        await loadingIndicator.Hide();
    }
}
```

### Disabling input controls

While the busy screen prevents click events from reaching child content it has no effect on keyboard input. You may want to disable your input controls such as textboxes and buttons while your component is busy.

Using the  property directly.

```
<LoadingIndicator @ref="loadingIndicator">
    <Button Disabled="loadingIndicator.Visible" Clicked="DoWork"/>
</LoadingIndicator>
```

```
@code
{
    LoadingIndicator loadingIndicator;

    async Task DoWork()
    {
        if ( !loadingIndicator.Visible )
        {
            await loadingIndicator.Show();
            
            // do work...
            
            await loadingIndicator.Hide();
        }
    }
}
```

Disabling your controls using .

```
@inject ILoadingIndicatorService ApplicationLoadingIndicatorService

<Button Disabled="ApplicationLoadingIndicatorService.Visible" />
```

```
@inject ILoadingIndicatorService ApplicationLoadingIndicatorService

<form action="/action_page.php">
    <fieldset disabled="ApplicationLoadingIndicatorService.Visible"> 
        <label for="fname">Message:</label>
        <input type="text" id="message" name="message">
        <input type="submit" value="Send">
     </fieldset>
</form>
```

### Using animation

Loading indicator can animate its visibility state by fading into view. This is on by default for . You can also use the  component to add a visual effect.

```
<LoadingIndicator @ref="loadingIndicator" FullScreen FadeIn>
    <ChildContent>
        <Button Clicked="ShowIndicator" Color="Color.Primary">Show indicator</Button>
    </ChildContent>
    <IndicatorTemplate>
        <Animate Animation="Animations.FadeDownRight" Auto Duration="TimeSpan.FromMilliseconds( 700 )">
            <Div>
                <SpinKit Type="SpinKitType.Wave" Size="100px" />
            </Div>
        </Animate>
    </IndicatorTemplate>
</LoadingIndicator>
```

```
@code
{
    LoadingIndicator loadingIndicator;

    async Task ShowIndicator()
    {
        await loadingIndicator.Show();

        await Task.Delay( 3000 ); // Do work ...

        await loadingIndicator.Hide();
    }
}
```

## API

### Parameters

| Parameter                    | Description                                                                         | Type                      | Default                          |
|------------------------------|-------------------------------------------------------------------------------------|---------------------------|----------------------------------|
| ChildContent                 | Specifies the content to be rendered inside this LoadingIndicator.LoadingIndicator. | RenderFragment            | null                             |
| FadeIn                       | Fade in indicator into view.                                                        | bool                      | false                            |
| FadeInDuration               | Fade in duration in milliseconds. Default is 700 ms.                                | TimeSpan                  | TimeSpan.FromMilliseconds( 700 ) |
| FullScreen                   | Show busy indicator full screen.                                                    | bool                      | false                            |
| IndicatorBackground          | Busy screen color.                                                                  | Background                | "rgba(255, 255, 255, 0.7)"       |
| IndicatorHorizontalPlacement | Indicator horizontal position.Possible values:Top, Bottom, Start, End, Middle       | LoadingIndicatorPlacement | LoadingIndicatorPlacement.Middle |
| IndicatorPadding             | Indicator div padding.                                                              | IFluentSpacing            | null                             |
| IndicatorTemplate            | Busy indicator template.                                                            | RenderFragment            | null                             |
| IndicatorVerticalPlacement   | Indicator vertical position.Possible values:Top, Bottom, Start, End, Middle         | LoadingIndicatorPlacement | LoadingIndicatorPlacement.Middle |
| Initializing                 | Indicates whether component should display initializing or actual content.          | bool                      | false                            |
| InitializingTemplate         | Loading state template.                                                             | RenderFragment            | null                             |
| Inline                       | Wrap inline content.                                                                | bool                      | false                            |
| Service                      | Service used to control this instance.                                              | ILoadingIndicatorService  | null                             |
| SpinnerBackground            | Spinner background color.                                                           | Background                | "#c0c0c0"                        |
| SpinnerColor                 | Defines the spinner color in a HEX format.                                          | Color                     | "#000000"                        |
| SpinnerHeight                | Defines the spinner HTML height, eg. "64px".                                        | string                    | "64px"                           |
| SpinnerWidth                 | Defines the spinner HTML width, eg. "64px".                                         | string                    |                                  |
| Visible                      | Indicates whether the loading indicator is visible.                                 | bool                      | false                            |
| ZIndex                       | Overlay screen z-index.                                                             | int?                      | null                             |

### Events

| Event               | Description                                 | Type                |
|---------------------|---------------------------------------------|---------------------|
| InitializingChanged | Occurs when Initializing state has changed. | EventCallback<bool> |
| VisibleChanged      | Occurs when Visible state has changed.      | EventCallback<bool> |

### Methods

| Method          | Description                | Return   | Parameters   |
|-----------------|----------------------------|----------|--------------|
| Show            | Show loading indicator     | Task     |              |
| Hide            | Hide loading indicator     | Task     |              |
| SetInitializing | Set component Loaded state | Task     | bool value   |

###### On this page

#### 

## 