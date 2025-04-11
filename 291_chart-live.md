# Blazorise Chart Streaming

Chart plugin for live streaming data.

📊 The Community License has a limitation of 10 points per chart. Unlock full access to all features with
    
        our premium plans.

Live streaming is made possible with the help of chartjs-plugin-streaming.

## Installation

### NuGet

Install chart streaming extension from NuGet.

```
Install-Package Blazorise.Charts.Streaming
```

### Static Files

Include the necessary files into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<script src="https://cdn.jsdelivr.net/npm/luxon@1.28.1"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-luxon@1.0.0"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-streaming@2.0.0"></script>
```

## Examples

### Basic Example

```
<LineChart @ref="horizontalLineChart" TItem="LiveDataPoint" OptionsObject="@horizontalLineChartOptions">
    <ChartStreaming TItem="LiveDataPoint"
                    Options="new ChartStreamingOptions { Delay = 2000 }"
                    Refreshed="@OnHorizontalLineRefreshed" />
</LineChart>
```

```
@code{
    LineChart<LiveDataPoint> horizontalLineChart;
    Random random = new Random( DateTime.Now.Millisecond );

    string[] Labels = { "Red", "Blue", "Yellow", "Green", "Purple", "Orange" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    public struct LiveDataPoint
    {
        public object X { get; set; }

        public object Y { get; set; }
    }

    object horizontalLineChartOptions = new
    {
        Scales = new
        {
            Y = new
            {
                Title = new
                {
                    Display = true,
                    Text = "Value"
                }
            }
        },
        Interaction = new
        {
            intersect = false
        }
    };

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await Task.WhenAll(
                HandleRedraw( horizontalLineChart, GetLineChartDataset1 ) );
        }
    }

    async Task HandleRedraw<TDataSet, TItem, TOptions, TModel>( BaseChart<TDataSet, TItem, TOptions, TModel> chart, params Func<TDataSet>[] getDataSets )
        where TDataSet : ChartDataset<TItem>
        where TOptions : ChartOptions
        where TModel : ChartModel
    {
        await chart.Clear();

        await chart.AddLabelsDatasetsAndUpdate( Labels, getDataSets.Select( x => x.Invoke() ).ToArray() );
    }

    LineChartDataset<LiveDataPoint> GetLineChartDataset1()
    {
        return new LineChartDataset<LiveDataPoint>
        {
            Data = new List<LiveDataPoint>(),
            Label = "Dataset 1 (linear interpolation)",
            BackgroundColor = backgroundColors[0],
            BorderColor = borderColors[0],
            Fill = false,
            Tension = 0,
            BorderDash = new List<int> { 8, 4 },
        };
    }

    Task OnHorizontalLineRefreshed( ChartStreamingData<LiveDataPoint> data )
    {
        data.Value = new LiveDataPoint
        {
            X = DateTime.Now,
            Y = RandomScalingFactor(),
        };

        return Task.CompletedTask;
    }

    double RandomScalingFactor()
    {
        return ( random.NextDouble() > 0.5 ? 1.0 : -1.0 ) * Math.Round( random.NextDouble() * 100 );
    }
}
```

### Pause/Play

Making the stream pause and play is very simple. You only need to add a  to the  and the call  or  methods.

```
<LineChart @ref="@horizontalLineChart" TItem="LiveDataPoint" OptionsObject="@horizontalLineChartOptions">
    <ChartStreaming @ref="@chartStreaming"
                    TItem="LiveDataPoint"
                    Options="new ChartStreamingOptions { Delay = 2000 }"
                    Refreshed="@OnHorizontalLineRefreshed" />
</LineChart>

<Row>
    <Column>
        <Button Color="Color.Primary" Clicked="@(()=>chartStreaming.Pause())">Pause</Button>
        <Button Color="Color.Primary" Clicked="@(()=>chartStreaming.Play())">Play</Button>
    </Column>
</Row>
```

```
@code{
    LineChart<LiveDataPoint> horizontalLineChart;
    ChartStreaming<LiveDataPoint>  chartStreaming;
    Random random = new Random( DateTime.Now.Millisecond );

    string[] Labels = { "Red", "Blue", "Yellow", "Green", "Purple", "Orange" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    public struct LiveDataPoint
    {
        public object X { get; set; }

        public object Y { get; set; }
    }

    object horizontalLineChartOptions = new
    {
        Scales = new
        {
            Y = new
            {
                Title = new
                {
                    Display = true,
                    Text = "Value"
                }
            }
        },
        Interaction = new
        {
            intersect = false
        }
    };

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await Task.WhenAll(
                HandleRedraw( horizontalLineChart, GetLineChartDataset1 ) );
        }
    }

    async Task HandleRedraw<TDataSet, TItem, TOptions, TModel>( BaseChart<TDataSet, TItem, TOptions, TModel> chart, params Func<TDataSet>[] getDataSets )
        where TDataSet : ChartDataset<TItem>
        where TOptions : ChartOptions
        where TModel : ChartModel
    {
        await chart.Clear();

        await chart.AddLabelsDatasetsAndUpdate( Labels, getDataSets.Select( x => x.Invoke() ).ToArray() );
    }

    LineChartDataset<LiveDataPoint> GetLineChartDataset1()
    {
        return new LineChartDataset<LiveDataPoint>
        {
            Data = new List<LiveDataPoint>(),
            Label = "Dataset 1 (linear interpolation)",
            BackgroundColor = backgroundColors[0],
            BorderColor = borderColors[0],
            Fill = false,
            Tension = 0,
            BorderDash = new List<int> { 8, 4 },
        };
    }

    Task OnHorizontalLineRefreshed( ChartStreamingData<LiveDataPoint> data )
    {
        data.Value = new LiveDataPoint
        {
            X = DateTime.Now,
            Y = RandomScalingFactor(),
        };

        return Task.CompletedTask;
    }

    double RandomScalingFactor()
    {
        return ( random.NextDouble() > 0.5 ? 1.0 : -1.0 ) * Math.Round( random.NextDouble() * 100 );
    }
}
```

## API

### Parameters

| Parameter   | Description                                  | Type                  | Default   |
|-------------|----------------------------------------------|-----------------------|-----------|
| Options     | Defines the stream options.                  | ChartStreamingOptions | new()     |
| Vertical    | If true, chart will be set to vertical mode. | bool                  | false     |

### Events

| Event     | Description                                                                                                                                                                                                                  | Type                                     |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| Refreshed | Callback function that will be called at a regular interval. The callback takes one argument, a reference to the dataset object. You can update your datasets here. The chart will be automatically updated after returning. | EventCallback<ChartStreamingData<TItem>> |

### Methods

| Method   | Description                         | Return   | Parameters   |
|----------|-------------------------------------|----------|--------------|
| Refresh  | Refreshes the chart with new data.  | Task     |              |
| Pause    | Pauses the current chart streaming. | Task     | bool animate |
| Play     | Plays the current chart streaming.  | Task     | bool animate |

###### On this page

#### 

## 