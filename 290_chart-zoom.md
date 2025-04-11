# Blazorise Chart Zoom

Zoom and pan the chart with the zoom plugin.

📊 The Community License has a limitation of 10 points per chart. Unlock full access to all features with
    
        our premium plans.

Zoom is made possible with the help of chartjs-plugin-zoom.

## Installation

### NuGet

Install the charts extension and plugin from NuGet.

```
Install-Package Blazorise.Charts
Install-Package Blazorise.Chart.Zoom
```

### Static Files

Include the necessary files into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<script src="https://cdn.jsdelivr.net/npm/hammerjs@2.0.8"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-zoom@2.0.1/dist/chartjs-plugin-zoom.min.js"></script>
```

chartjs-plugin-zoom must be loaded after the Chart.js library!

.

## Examples

### Basic

```
<Button Color="Color.Primary" Clicked="@(async () => await HandleRedraw())">Redraw</Button>

<LineChart @ref="lineChart" TItem="double">
    <ChartZoom TItem="double" Options="@lineChartZoomOptions" />
</LineChart>
```

```
@code {
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

    private ChartZoomPluginOptions lineChartZoomOptions = new()
        {
            Zoom = new()
            {
                Mode = "y",
                Wheel = new()
                {
                    Enabled = true,
                },
                Pinch = new()
                {
                    Enabled = true
                },
                Drag = new()
                {
                    Enabled = true
                }
            },
            Limits = new()
            {
                Y = new()
                {
                    Min = 0,
                    Max = 50,
                    MinRange = 25
                }
            },
            Transition = new ChartZoomTransitionOptions()
            {
                Animation = new ChartAnimation()
                {
                    Duration = 1000,
                    Easing = "easeOutCubic"
                }
            }
        };
}
```

## API

### Parameters

| Parameter   | Description                            | Type                   | Default   |
|-------------|----------------------------------------|------------------------|-----------|
| Options     | Defines the options for an annotation. | ChartZoomPluginOptions | null      |

### Options

#### ChartZoomPluginOptions

| Name       | Description        | Type                   | Default   |
|------------|--------------------|------------------------|-----------|
| Zoom       | Zoom options       | ChartZoomOptions       |           |
| Pan        | Pan options        | ChartZoomPanOptions    |           |
| Limits     | Limits options     | ChartZoomLimitsOptions |           |
| Transition | Transition options | ChartZoomTransition    |           |

#### ChartZoomOptions

| Name      | Description                                                                                                          | Type           | Default   |
|-----------|----------------------------------------------------------------------------------------------------------------------|----------------|-----------|
| Wheel     | The Wheel options                                                                                                    | ChartZoomWheel | null      |
| Drag      | The Drag options                                                                                                     | ChartZoomDrag  | null      |
| Pinch     | The Pinch options                                                                                                    | ChartZoomPinch | null      |
| Mode      | Allowed zoom directions                                                                                              | string         | null      |
| ScaleMode | Which of the enabled zooming directions should only be available when the mouse cursor is over a scale for that axis | string         | null      |

#### ChartZoomWheelOptions

| Name        | Description                                       | Type    | Default   |
|-------------|---------------------------------------------------|---------|-----------|
| Enabled     | Enable zooming via mouse wheel                    | bool?   | null      |
| Speed       | Factor of zoom speed via mouse wheel              | double? | null      |
| ModifierKey | Modifier key required for zooming via mouse wheel | string  | null      |

#### ChartZoomDragOptions

| Name            | Description                                                  | Type    | Default   |
|-----------------|--------------------------------------------------------------|---------|-----------|
| Enabled         | Enable drag-to-zoom                                          | bool?   | null      |
| BackgroundColor | Fill color                                                   | string  | null      |
| BorderColor     | Stroke color                                                 | string  | null      |
| BorderWidth     | Stroke width                                                 | double? | null      |
| Threshold       | Minimal zoom distance required before actually applying zoom | double? | null      |
| ModifierKey     | Modifier key required for drag-to-zoom                       | string  | null      |

#### ChartZoomPinchOptions

| Name    | Description              | Type   | Default   |
|---------|--------------------------|--------|-----------|
| Enabled | Enable zooming via pinch | bool?  | null      |

#### ChartZoomPanOptions

| Name        | Description                                                    | Type    | Default   |
|-------------|----------------------------------------------------------------|---------|-----------|
| Enabled     | Enable panning                                                 | bool?   | null      |
| Mode        | Allowed panning directions                                     | string  | null      |
| ModifierKey | Modifier key required for panning with mouse                   | string  | null      |
| ScaleMode   | Enable panning over a scale for that axis (regardless of mode) | double? | null      |
| Threshold   | Minimal pan distance required before actually applying pan     | double? | null      |

#### ChartZoomLimitsOptions

| Name   | Description       | Type                 | Default   |
|--------|-------------------|----------------------|-----------|
| X      | Limits for x-axis | ChartZoomScaleLimits | null      |
| Y      | Limits for y-axis | ChartZoomScaleLimits | null      |

#### ChartZoomScaleLimitsOptions

| Name     | Description                                                         | Type    | Default   |
|----------|---------------------------------------------------------------------|---------|-----------|
| Min      | Minimum allowed value for scale.min                                 | double? | null      |
| Max      | Maximum allowed value for scale.max                                 | double? | null      |
| MinRange | Minimum allowed range (max - min). This defines the max zoom level. | double? | null      |

###### On this page

#### 

## 