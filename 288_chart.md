# Blazorise Chart component

Simple yet flexible charting for designers &amp; developers.

📊 The Community License has a limitation of 10 points per chart. Unlock full access to all features with
    
        our premium plans.

The chart extension is defined of several different chart components. Each of the chart type have it’s own dataset and option settings.

Supported charts types are:

- Chart default chart components, should be used only for testing(see warning)
- LineChart
- BarChart
- PieChart
- PolarAreaChart
- DoughnutChart
- RadarChart

## Installation

### NuGet

Install chart extension from NuGet.

```
Install-Package Blazorise.Charts
```

### Imports

In your main  add:

```
@using Blazorise.Charts
```

### Static Files

Add  and  to your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js"></script>
```

### Example

You should always define  data type.

```
<Button Color="Color.Primary" Clicked="@(async () => await HandleRedraw())">Redraw</Button>

<LineChart @ref="lineChart" TItem="double" />
```

```
@code{
    LineChart<double> lineChart;

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await HandleRedraw();
        }
    }

    async Task HandleRedraw()
    {
        await lineChart.Clear();

        await lineChart.AddLabelsDatasetsAndUpdate( Labels, GetLineChartDataset() );
    }

    LineChartDataset<double> GetLineChartDataset()
    {
        return new LineChartDataset<double>
        {
            Label = "# of randoms",
            Data = RandomizeData(),
            BackgroundColor = backgroundColors,
            BorderColor = borderColors,
            Fill = true,
            PointRadius = 3,
            CubicInterpolationMode = "monotone",
        };
    }

    string[] Labels = { "Red", "Blue", "Yellow", "Green", "Purple", "Orange" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    List<double> RandomizeData()
    {
        var r = new Random( DateTime.Now.Millisecond );

        return new List<double> { 
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble() };
    }
}
```

### Events

It is possible to use

and

events to interact with chart. The usage is pretty straightforward. The only thing to keep in mind is the

field that needs to be casted to the right chart-model type. The available model types are:

- LineChartModel
- BarChartModel
- DoughnutChartModel
- PieChartModel
- PolarChartModel
- RadarChartModel

```
<Chart @ref="barChart" Type="ChartType.Bar" TItem="double" Clicked="@OnClicked" />
```

```
@code {
    Chart<double> barChart;

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await HandleRedraw();
        }
    }

    async Task HandleRedraw()
    {
        await barChart.Clear();

        await barChart.AddLabelsDatasetsAndUpdate( Labels, GetBarChartDataset() );
    }

    private BarChartDataset<double> GetBarChartDataset()
    {
        return new()
            {
                Label = "# of randoms",
                Data = RandomizeData(),
                BackgroundColor = backgroundColors,
                BorderColor = borderColors,
                BorderWidth = 1
            };
    }

    string[] Labels = { "Red", "Blue", "Yellow", "Green", "Purple", "Orange" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    List<double> RandomizeData()
    {
        var r = new Random( DateTime.Now.Millisecond );

        return new List<double> {
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble(),
            r.Next( 3, 50 ) * r.NextDouble() };
    }

    Task OnClicked( ChartMouseEventArgs e )
    {
        var model = e.Model as BarChartModel;

        Console.WriteLine( $"Handling event for {nameof( BarChartModel )}: x:{model.X} y:{model.Y}" );
        return Task.CompletedTask;
    }
}
```

### Complex Data

We also support the usage complex-type as chart data. To represent the complex-type inside of the charts you need to define the Parsing options.

```
<LineChart @ref="lineChart" TItem="WatcherEvent" Options="@lineChartOptions" />
```

```
@code {
    private LineChart<WatcherEvent> lineChart;

    LineChartOptions lineChartOptions = new()
    {
        Parsing = new ChartParsing
        {
            XAxisKey = "sector",
            YAxisKey = "count",
        }
    };

    private List<string> backgroundColors = new() { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    private List<string> borderColors = new() { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    private bool isAlreadyInitialised;

    public class WatcherEvent
    {
        public string Sector { get; set; }

        public int Count { get; set; }

        public DateTime Date { get; } = DateTime.Now;
    }

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( !isAlreadyInitialised )
        {
            isAlreadyInitialised = true;

            await lineChart.Clear();
            await lineChart.AddDataSet( GetLineChartDataset() );
        }
    }

    private LineChartDataset<WatcherEvent> GetLineChartDataset()
    {
        return new()
        {
            Label = "# of randoms",
            Data = new List<WatcherEvent>
            {
                new WatcherEvent { Sector = "A", Count = 1400 },
                new WatcherEvent { Sector = "B", Count = 900 },
                new WatcherEvent { Sector = "C", Count = 1800 },
                new WatcherEvent { Sector = "D", Count = 1300 },
            },
            BackgroundColor = backgroundColors[0], // line chart can only have one color
            BorderColor = borderColors[0],
            Fill = true,
            PointRadius = 3,
            BorderWidth = 1,
            PointBorderColor = Enumerable.Repeat( borderColors.First(), 6 ).ToList(),
            CubicInterpolationMode = "monotone",
        };
    }
}
```

### Horizontal Bar Chart

By adjusting the  and changing the  you can make the horizontal Bar Chart.

```
<Button Color="Color.Primary" Clicked="@(async () => await HandleRedraw())">Redraw</Button>

<BarChart @ref="barChart" TItem="double" Options="@options" />
```

```
@code {
    BarChart<double> barChart;

    BarChartOptions options = new()
    {
        IndexAxis = "y",
        Elements = new()
        {
            Bar = new()
            {
                BorderWidth = 2,
            }
        },
        Responsive = true,
        Plugins = new()
        {
            Legend = new()
            {
                Position = "right"
            },
            Title = new()
            {
                Display = true,
                    Text = "Chart.js Horizontal Bar Chart"
            }
        }
    };

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await HandleRedraw();
        }
    }

    async Task HandleRedraw()
    {
        await barChart.Clear();

        await barChart.AddLabelsDatasetsAndUpdate( Labels,
            GetBarChartDataset( "Dataset 1" ),
            GetBarChartDataset( "Dataset 2" ) );
    }

    BarChartDataset<double> GetBarChartDataset( string label )
    {
        return new BarChartDataset<double>
        {
            Label = label,
            Data = RandomizeData(),
            BackgroundColor = backgroundColors,
            BorderColor = borderColors,
        };
    }

    string[] Labels = { "Red", "Blue", "Yellow", "Green", "Purple", "Orange" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };
    Random random = new Random( DateTime.Now.Millisecond );

    List<double> RandomizeData()
    {
        return new List<double> {
            random.Next( -50, 50 ) * random.NextDouble(),
            random.Next( -50, 50 ) * random.NextDouble(),
            random.Next( -50, 50 ) * random.NextDouble(),
            random.Next( -50, 50 ) * random.NextDouble(),
            random.Next( -50, 50 ) * random.NextDouble(),
            random.Next( -50, 50 ) * random.NextDouble() };
    }
}
```

## API

### Parameters

| Parameter         | Description                                                                                        | Type             | Default        |
|-------------------|----------------------------------------------------------------------------------------------------|------------------|----------------|
| ChildContent      | Specifies the content to render inside this Charts.Chart.                                          | RenderFragment   | null           |
| Data              | Defines the chart data.                                                                            | ChartData<TItem> | null           |
| DataJsonString    | Defines the chart data that is serialized as json string.                                          | string           |                |
| Options           | Defines the chart options.                                                                         | TOptions         | null           |
| OptionsJsonString | Defines the chart options that is serialized as json string.                                       | string           |                |
| OptionsObject     | Defines the chart options that is serialized as json object.                                       | object           | null           |
| Type              | Defines the chart type.Possible values:Line, Bar, Pie, Doughnut, PolarArea, Radar, Scatter, Bubble | ChartType        | ChartType.Line |

### Events

| Event    | Description                              | Type                               |
|----------|------------------------------------------|------------------------------------|
| Clicked  | Raised when clicked on data point.       | EventCallback<ChartMouseEventArgs> |
| Hovered  | Raised when hovered over data point.     | EventCallback<ChartMouseEventArgs> |
| MouseOut | Raised when mouse leaves the chart area. | EventCallback<ChartMouseEventArgs> |

### Methods

| Method                     | Description                                                                                                                                                                                                                                                    | Return   | Parameters                                              |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|---------------------------------------------------------|
| Clear                      | Clears all the labels and data from the chart.                                                                                                                                                                                                                 | Task     |                                                         |
| AddLabels                  | Adds a new label to the chart.                                                                                                                                                                                                                                 | Task     | object[] labels                                         |
| AddDataSet                 | Adds a new dataset to the chart.                                                                                                                                                                                                                               | Task     | TDataSet[] datasets                                     |
| RemoveDataSet              | Removed the dataset at the specified index.                                                                                                                                                                                                                    | Task     | int dataSetIndex                                        |
| SetData                    | Sets the new data point(s) to the specified dataset.                                                                                                                                                                                                           | Task     | int dataSetIndex, List<TItem> data                      |
| AddData                    | Adds the new data point(s) to the specified dataset.                                                                                                                                                                                                           | Task     | int dataSetIndex, TItem[] data                          |
| AddDatasetsAndUpdate       | Adds new datasets and then update the chart.                                                                                                                                                                                                                   | Task     | TDataSet[] datasets                                     |
| AddLabelsDatasetsAndUpdate | Adds new set of labels and datasets and then update the chart.                                                                                                                                                                                                 | Task     | IReadOnlyCollection<object> labels, TDataSet[] datasets |
| ShiftLabel                 | Removes the oldest label.                                                                                                                                                                                                                                      | Task     |                                                         |
| ShiftData                  | Removes the oldest data point from the specified dataset.                                                                                                                                                                                                      | Task     | int dataSetIndex                                        |
| PopLabel                   | Removes the newest label.                                                                                                                                                                                                                                      | Task     |                                                         |
| PopData                    | Removes the newest data point from the specified dataset.                                                                                                                                                                                                      | Task     | int dataSetIndex                                        |
| SetOptions                 | Sets the chart's options manually. Must call Update after making this call.  If the options changes AspectRatio must also call Resize after Update.                                                                                                            | Task     | TOptions options                                        |
| SetOptionsObject           | Sets the chart's Charts.BaseChart.OptionsObject manually. Must call Charts.BaseChart.Update after manging this call.     If the options changes AspectRatio must also call Charts.BaseChart.Resize after Charts.BaseChart.Update.                              | Task     | object optionsObject                                    |
| Resize                     | Manually resize the canvas element. This is run each time the canvas container is resized,      but you can call this method manually if you change the size of the canvas nodes container element.      Should also be called when updating the aspect ratio. | Task     |                                                         |
| ChangeType                 | Destroy the current chart instance and recreates it by using the same data and options.                                                                                                                                                                        | Task     | ChartType type                                          |
| Destroy                    | Destroys the chart instance. Calling this method should generally dispose of any chart resources.                                                                                                                                                              | Task     |                                                         |
| Update                     | Update and redraw the chart.                                                                                                                                                                                                                                   | Task     |                                                         |
| NotifyPluginInitialized    | Notifies the chart that it contains the plugin.                                                                                                                                                                                                                | void     | string pluginName                                       |
| NotifyPluginRemoved        | Notifies the chart that it should remove the plugin.                                                                                                                                                                                                           | void     | string pluginName                                       |

## Options

### ChartOptions

| Name                | Description                                                                                                                     | Type             | Default   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------|------------------|-----------|
| Scales              | Configuration for chart scales.                                                                                                 | ChartScales      | null      |
| Animation           | Configuration for chart animation.                                                                                              | ChartAnimation   | null      |
| Plugins             | Configuration for chart plugins.                                                                                                | ChartPlugins     | null      |
| Interaction         | Configuration for chart interactions.                                                                                           | ChartInteraction | null      |
| Parsing             | Configuration for chart parsing.                                                                                                | ChartParsing     | null      |
| Elements            | Configuration for chart elements.                                                                                               | ChartElements    | null      |
| Layout              | Configuration for chart layout.                                                                                                 | ChartLayout      | null      |
| IndexAxis           | Index axis for the chart.                                                                                                       | string           | null      |
| Responsive          | Resizes the chart canvas when its container does.                                                                               | bool?            | null      |
| MaintainAspectRatio | Maintain the original canvas aspect ratio (width / height) when resizing.                                                       | bool?            | null      |
| AspectRatio         | Canvas aspect ratio (i.e. width / height, a value of 1 representing a square canvas).         Note that this option is ignored if the height is explicitly defined either as attribute or via the style.                                                                                                                                 | double?          | null      |
| ResizeDelay         | Delay the resize update by given amount of milliseconds. This can ease the resize process by debouncing update of the elements. | int?             | null      |
| Locale              | A string with a BCP 47 language tag, leveraging on .                                                                            | string           | null      |

### ChartScales

| Name   | Description                   | Type      | Default   |
|--------|-------------------------------|-----------|-----------|
| X      | Configuration for the x-axis. | ChartAxis | null      |
| Y      | Configuration for the y-axis. | ChartAxis | null      |

### ChartAnimation

| Name     | Description                                    | Type   | Default   |
|----------|------------------------------------------------|--------|-----------|
| Duration | The number of milliseconds an animation takes. | int?   | null      |
| Easing   | Easing function to use. more...                | string | null      |
| Delay    | Delay before starting the animations.          | int?   | null      |
| Loop     | If set to true, the animations loop endlessly. | bool?  | null      |

### ChartPlugins

| Name       | Description                              | Type            | Default   |
|------------|------------------------------------------|-----------------|-----------|
| Legend     | Configuration for the chart legend.      | ChartLegend     | null      |
| Tooltips   | Configuration for the chart tooltips.    | ChartTooltips   | null      |
| Title      | Configuration for the chart title.       | ChartTitle      | null      |
| Subtitle   | Configuration for the chart subtitle.    | ChartSubtitle   | null      |
| Decimation | Configuration for chart data decimation. | ChartDecimation | null      |

### ChartInteraction

| Name      | Description                                                                                                                                                             | Type   | Default   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| Mode      | Sets which elements appear in the interaction.                                                                                                                          | string | null      |
| Intersect | If true, the interaction mode only applies when the mouse position intersects an item on the chart.                                                                     | bool?  | null      |
| Axis      | Can be set to 'x', 'y', or 'xy' to define which directions are used in calculating distances. Defaults to 'x' for 'index' mode and 'xy' in dataset and 'nearest' modes. | string | null      |

### ChartParsing

| Name     | Description                            | Type   | Default   |
|----------|----------------------------------------|--------|-----------|
| XAxisKey | Key for the x-axis values in the data. | string | null      |
| YAxisKey | Key for the y-axis values in the data. | string | null      |

### ChartLayout

| Name        | Description                                                       | Type         | Default   |
|-------------|-------------------------------------------------------------------|--------------|-----------|
| AutoPadding | Apply automatic padding so visible elements are completely drawn. | bool?        | null      |
| Padding     | The padding to add inside the chart.                              | ChartPadding | null      |

### ChartElements

| Name   | Description                                                                       | Type               | Default   |
|--------|-----------------------------------------------------------------------------------|--------------------|-----------|
| Point  | Point elements are used to represent the points in a line, radar or bubble chart. | ChartPointElements | null      |
| Line   | Line elements are used to represent the line in a line chart.                     | ChartLineElements  | null      |
| Bar    | Bar elements are used to represent the bars in a bar chart.                       | ChartBarElements   | null      |
| Arc    | Arcs are used in the polar area, doughnut and pie charts.                         | ChartArcElements   | null      |

### ChartLegend

| Name          | Description                                                                                                                                         | Type             | Default   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-----------|
| Display       | Is the legend shown.                                                                                                                                | bool?            | null      |
| Position      | Position of the legend.                                                                                                                             | string           | null      |
| Align         | Alignment of the legend.                                                                                                                            | string           | null      |
| MaxHeight     | Maximum height of the legend, in pixels.                                                                                                            | int?             | null      |
| MaxWidth      | Maximum width of the legend, in pixels.                                                                                                             | int?             | null      |
| FullSize      | Marks that this box should take the full width/height of the canvas (moving other boxes). This is unlikely to need to be changed in day-to-day use. | bool?            | null      |
| Reverse       | Legend will show datasets in reverse order.                                                                                                         | bool?            | null      |
| Labels        | Options to change legend labels.                                                                                                                    | ChartLegendLabel | null      |
| Rtl           | true for rendering the legends from right to left.                                                                                                  | bool?            | null      |
| TextDirection | This will force the text direction 'rtl' or 'ltr' on the canvas for rendering the legend, regardless of the css specified on the canvas.            | string           | null      |
| Title         | Options to change legend title.                                                                                                                     | ChartLegendTitle | null      |

### ChartTooltips

| Name               | Description                                                                                                                                                                   | Type                    | Default                           |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|-----------------------------------|
| Enabled            | Are on-canvas tooltips enabled.                                                                                                                                               | bool?                   | null                              |
| Mode               | Sets which elements appear in the tooltip.                                                                                                                                    | string                  | null                              |
| Intersect          | If true, the tooltip mode applies only when the mouse position intersects with an element. If false, the mode will be applied at all times.                                   | bool?                   | null                              |
| Position           | The mode for positioning the tooltip.                                                                                                                                         | string                  | null                              |
| BackgroundColor    | Background color of the tooltip.                                                                                                                                              | IndexableOption<object> | null                              |
| TitleColor         | Color of title text.                                                                                                                                                          | IndexableOption<object> | null                              |
| TitleFont          | See Fonts.                                                                                                                                                                    | ChartFont               | new ChartFont { Weight = "bold" } |
| TitleAlign         | Horizontal alignment of the title text lines.                                                                                                                                 | string                  | null                              |
| TitleSpacing       | Spacing to add to top and bottom of each title line.                                                                                                                          | int?                    | null                              |
| TitleMarginBottom  | Margin to add on bottom of title section.                                                                                                                                     | int?                    | null                              |
| BodyColor          | Color of body text.                                                                                                                                                           | IndexableOption<object> | null                              |
| BodyFont           | See Fonts.                                                                                                                                                                    | ChartFont               | null                              |
| BodyAlign          | Horizontal alignment of the body text lines.                                                                                                                                  | string                  | null                              |
| BodySpacing        | Spacing to add to top and bottom of each tooltip item.                                                                                                                        | int?                    | null                              |
| FooterColor        | Color of footer text.                                                                                                                                                         | IndexableOption<object> | null                              |
| FooterFont         | See Fonts.                                                                                                                                                                    | ChartFont               | null                              |
| FooterAlign        | Horizontal alignment of the footer text lines.                                                                                                                                | string                  | null                              |
| FooterSpacing      | Spacing to add to top and bottom of each footer line.                                                                                                                         | int?                    | null                              |
| FooterMarginTop    | Margin to add before drawing the footer.                                                                                                                                      | int?                    | null                              |
| Padding            | Padding inside the tooltip.                                                                                                                                                   | object                  | null                              |
| CaretPadding       | Extra distance to move the end of the tooltip arrow away from the tooltip point.                                                                                              | object                  | null                              |
| CaretSize          | Size, in px, of the tooltip arrow.                                                                                                                                            | int?                    | null                              |
| CornerRadius       | Radius of tooltip corner curves.                                                                                                                                              | int?                    | null                              |
| MultiKeyBackground | Color to draw behind the colored boxes when multiple items are in the tooltip.                                                                                                | IndexableOption<object> | null                              |
| DisplayColors      | If true, color boxes are shown in the tooltip.                                                                                                                                | bool?                   | null                              |
| BoxWidth           | Width of the color box if displayColors is true.                                                                                                                              | int?                    | null                              |
| BoxHeight          | Height of the color box if displayColors is true.                                                                                                                             | int?                    | null                              |
| BoxPadding         | Padding between the color box and the text.                                                                                                                                   | int?                    | null                              |
| UsePointStyle      | Use the corresponding point style (from dataset options) instead of color boxes, ex: star, triangle etc. (size is based on the minimum value between boxWidth and boxHeight). | bool?                   | null                              |
| BorderColor        | Color of the border.                                                                                                                                                          | IndexableOption<object> | null                              |
| BorderWidth        | Size of the border.                                                                                                                                                           | int?                    | null                              |
| Rtl                | true for rendering the tooltip from right to left.                                                                                                                            | bool?                   | null                              |
| TextDirection      | This will force the text direction 'rtl' or 'ltr on the canvas for rendering the tooltips, regardless of the css specified on the canvas.                                     | string                  | null                              |
| XAlign             | Position of the tooltip caret in the X direction.         "left" (default)              "center" "right"                                                                                                                                                                               | string                  | null                              |
| YAlign             | Position of the tooltip caret in the Y direction.         "left" (default)              "center" "right"                                                                                                                                                                               | string                  | null                              |

### ChartAxis

| Name          | Description                                                                                                                                                               | Type              | Default   |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-----------|
| Type          | Type of scale being employed. Custom scales can be created and registered with a string key. This allows changing the type of an axis for a chart.                        | string            | null      |
| AlignToPixels | Align pixel values to device pixels.                                                                                                                                      | bool?             | null      |
| Display       | Controls the axis global visibility (visible when true, hidden when false). When display: "auto", the axis is visible only if at least one associated dataset is visible. | bool              | true      |
| Grid          | Grid line configuration. more....                                                                                                                                         | ChartAxisGridLine |           |
| Min           | User defined minimum number for the scale, overrides minimum value from data. more...                                                                                     | double?           |           |
| Max           | User defined maximum number for the scale, overrides maximum value from data. more...                                                                                     | double?           |           |
| Reverse       | Reverse the scale.                                                                                                                                                        | bool?             |           |
| Stacked       | Should the data be stacked.                                                                                                                                               | bool?             |           |
| SuggestedMin  | Adjustment used when calculating the minimum data value. more...                                                                                                          | double?           |           |
| SuggestedMax  | Adjustment used when calculating the maximum data value. more...                                                                                                          | double?           |           |
| Ticks         | Tick configuration.                                                                                                                                                       | ChartAxisTicks    |           |
| Time          | Time configuration.                                                                                                                                                       | ChartAxisTime     |           |
| Weight        | The weight used to sort the axis. Higher weights are further away from the chart area.                                                                                    | double?           |           |
| Title         | Defines options for the scale title. Note that this only applies to cartesian axes.                                                                                       | ChartScaleTitle   |           |
| BeginAtZero   | If true, scale will include 0 if it is not already included.                                                                                                              | bool?             |           |
| Grace         | Percentage (string ending with %) or amount (number) for added room in the scale range above and below data.                                                              | object            |           |

### ChartAxisTicks

| Name              | Description                                                                                                         | Type                                            | Default   |
|-------------------|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|-----------|
| BackdropColor     | Color of label backdrops.                                                                                           | IndexableOption<object>                         | null      |
| BackdropPadding   | Padding of label backdrop. See more...                                                                              | object                                          | null      |
| Callback          | Defines the Expression which will be converted to JavaScript as a string representation of the tick value as it should be displayed on the chart.                       Eg. Callback = ( value, index, values ) => value / 1000 + "K"                                                                                                                     | Expression<Func<double, int, double[], string>> | null      |
| Display           | If true, show tick marks.                                                                                           | bool?                                           | null      |
| Color             | Color of ticks.                                                                                                     | IndexableOption<object>                         | null      |
| Font              | Font color for tick labels.                                                                                         | ChartFont                                       | null      |
| Major             | Major ticks configuration. Omitted options are inherited from options above.                                        | ChartAxisMajorTick                              | null      |
| Padding           | Sets the offset of the tick labels from the axis.                                                                   | double?                                         | null      |
| ShowLabelBackdrop | If true, draw a background behind the tick labels.                                                                  | bool?                                           | null      |
| TextStrokeColor   | The color of the stroke around the text.                                                                            | IndexableOption<object>                         | null      |
| TextStrokeWidth   | Stroke width around the text.                                                                                       | double?                                         | null      |
| Z                 | z-index of tick layer. Useful when ticks are drawn on chart area. Values <= 0 are drawn under datasets, > 0 on top. | double?                                         | null      |
| Count             | The number of ticks to generate. If specified, this overrides the automatic generation.                             | int?                                            | null      |
| Format            | The number format options used by the default label formatter.                                                      | object                                          | null      |
| Precision         | If defined and StepSize is not specified, the step size will be rounded to this many decimal places.                | double?                                         | null      |
| StepSize          | User-defined fixed step size for the scale.                                                                         | double?                                         | null      |

###### On this page

#### 

## 