# Blazorise Progress component

Progress bars are used to show the status of an ongoing operation.

Use our progress component for displaying simple or complex progress bars, featuring support for horizontally stacked bars, animated backgrounds, and text labels.

## Structure

- &lt; Progress&gt; main component for single progress value or wrapper for multiple bars.
- &lt;Progress&gt; main component for single progress value or wrapper for multiple bars.
    - &lt;ProgressBar&gt; progress bar for single progress value.

## Examples

Progress components are built with two components.

    
            We use the Progress as a wrapper to indicate the max value of the progress bar.
        

            We use the inner ProgressBar to indicate the progress so far.

### Single bar

Put that all together, and you have the following examples.

```
<Progress Value="25" />
```

### Multiple bars

Include multiple ProgressBar sub-components in a Progress component to build a horizontally stacked set of progress bars.

15

30

20

```
<Progress>
    <ProgressBar Value="15" />
    <ProgressBar Color="Color.Success" Value="30" />
    <ProgressBar Color="Color.Info" Value="20" />
</Progress>
```

### Animated

Use an animated effect Progress Bar to show that progress is still ongoing.

```
<Progress Value="75" Animated Striped />
```

### Indeterminate

Add a  to any  make the progres to the linear animation. Indeterminate Progress is best used to show that an operation is being executed.

```
<Progress Indeterminate />
```

### Max

You can specify the maximum value of the determinate Progress. This is useful for instances where you want to show capacity, or how much of a total has been uploaded/downloaded.

```
@using System.Timers
@implements IDisposable

<Field>
    <FieldBody>
        <Progress Max="42" Value="@Value" />
    </FieldBody>
    <FieldHelp>
        There have been @Value files downloaded
    </FieldHelp>
</Field>
```

```
@code {
    private int Value = 0;
    private Timer timer;

    private const int IntervalDelay = 100; // milliseconds
    private const int IntervalIncrement = 1;

    protected override void OnInitialized()
    {
        timer = new Timer(IntervalDelay);
        timer.Elapsed += OnTimerElapsed;
        timer.AutoReset = true;
        timer.Start();
    }

    private void OnTimerElapsed(object sender, ElapsedEventArgs e)
    {
        Value = Value < 42 ? Value + IntervalIncrement : 0;
        InvokeAsync(StateHasChanged);
    }

    public void Dispose()
    {
        timer?.Stop();
        timer?.Dispose();
    }
}
```

## Page progress

You can also show a small progress bar at the top of the page. Note that unlike regular Progress component,
    for PageProgress you must set the Visible parameter to make it active.

### Basic

To show page progress just set the  and  parameters.

```
<PageProgress Visible Value="25" />
```

### Indeterminate

To make an indeterminate progress bar, simply remove  or make it a .

```
<PageProgress Visible />
```

## API

### Parameters

#### Progress

| Parameter     | Description                                                | Type           | Default   |
|---------------|------------------------------------------------------------|----------------|-----------|
| Animated      | Set to true to make the progress bar animated.             | bool           | false     |
| ChildContent  | Specifies the content to be rendered inside this Progress. | RenderFragment | null      |
| Color         | Defines the progress bar color.                            | Color          | null      |
| Indeterminate | Set to true to show that an operation is being executed.   | bool           | false     |
| Max           | Maximum value of the progress bar.                         | int            | 0         |
| Min           | Minimum value of the progress bar.                         | int            | 0         |
| ShowValue     | If true, the value will be showed within the progress bar. | bool           | true      |
| Size          | Size of the progress bar.                                  | Size?          | null      |
| Striped       | Set to true to make the progress bar stripped.             | bool           | false     |
| Value         | The progress value.                                        | int?           | null      |

#### ProgressBar

| Parameter     | Description                                                   | Type           | Default       |
|---------------|---------------------------------------------------------------|----------------|---------------|
| Animated      | Set to true to make the progress bar animated.                | bool           | false         |
| ChildContent  | Specifies the content to be rendered inside this ProgressBar. | RenderFragment | null          |
| Color         | Defines the progress bar color.                               | Color          | Color.Primary |
| Indeterminate | Set to true to show that an operation is being executed.      | bool           | false         |
| Max           | Maximum value of the progress bar.                            | int            | 100           |
| Min           | Minimum value of the progress bar.                            | int            | 0             |
| Striped       | Set to true to make the progress bar stripped.                | bool           | false         |
| Value         | The progress value.                                           | int?           | null          |

#### PageProgress

| Parameter   | Description                                                       | Type   | Default       |
|-------------|-------------------------------------------------------------------|--------|---------------|
| Color       | Type color of the progress bar, optional.                         | Color  | Color.Default |
| Value       | The progress value. Leave as null for indeterminate progress bar. | int?   | null          |
| Visible     | Defines the visibility of progress bar.                           | bool   | false         |

### Methods

#### ProgressBar

| Method   | Description                                      | Return   | Parameters    |
|----------|--------------------------------------------------|----------|---------------|
| Animate  | Sets the progress bar ProgressBar.Animated flag. | Task     | bool animated |

#### PageProgress

| Method        | Description                                        | Return   | Parameters   |
|---------------|----------------------------------------------------|----------|--------------|
| SetValueAsync | Sets the progress value and redraws the component. | Task     | int? value   |

###### On this page

#### 

## 