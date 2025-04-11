# Blazorise Chart Trendline component

This plugin draws an linear trendline in your Chart.

📊 The Community License has a limitation of 10 points per chart. Unlock full access to all features with
    
        our premium plans.

Trendline is made possible with the help of chartjs-plugin-trendline.

## Installation

### NuGet

Install chart trendline extension from NuGet.

```
Install-Package Blazorise.Charts.Trendline
```

### Static Files

If you’re using Blazor WebAssembly, include these script references in your . If you're using Blazor Server, include them in your  /  file. Note: you may already have the chartjs reference in there. If so, only include the trendline script.

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-trendline"></script>
```

### Example

```
@using Blazorise.Charts
@using Blazorise.Charts.Trendline

<Button Color="Color.Primary" Clicked="@OnButtonClicked">Toggle trendline and redraw</Button>

<Chart @ref="chart" TItem="double?" Type="ChartType.Line">
    <ChartTrendline @ref="chartTrendline" TItem="double?" />
</Chart>
```

```
@code {
    Chart<double?> chart;
    ChartTrendline<double?> chartTrendline;

    protected override async Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await HandleRedraw();
        }
    }

    bool trendlinesOn = true;
    async Task OnButtonClicked()
    {
        trendlinesOn = !trendlinesOn;

        await HandleRedraw();
    }

    async Task HandleRedraw()
    {
        await chart.Clear();

        await chart.AddLabels( Labels );
        await chart.AddDataSet( GetLineChartDataset() );
        await chart.AddDataSet( GetLineChartDataset() );

        await chart.Update();

        // Add the trendline(s) after you have added the datasets and called await chart.Update();
        if ( trendlinesOn )
        {
            // This will add a trendline to the second dataset.
            // If you want to add it to the first dataset, set DatasetIndex = 0 (or don't set it at all as 0 is default)
            var trendlineData = new List<ChartTrendlineData>
            {
                new ChartTrendlineData
                {
                    DatasetIndex = 1,
                    Width = 10,
                    Color = ChartColor.FromRgba( 54, 162, 235, .6f )
                }
            };

            await chartTrendline.AddTrendLineOptions( trendlineData );
        }
    }

    LineChartDataset<double?> GetLineChartDataset()
    {
        return new LineChartDataset<double?>
            {
                Label = "# of randoms",
                Data = RandomizeData(),
                BackgroundColor = backgroundColors,
                BorderColor = borderColors,
                Fill = true,
                PointRadius = 2,
                BorderDash = new List<int> { }
            };
    }

    string[] Labels = { "0", "1", "2", "3", "4", "5" };
    List<string> backgroundColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 0.2f ), ChartColor.FromRgba( 54, 162, 235, 0.2f ), ChartColor.FromRgba( 255, 206, 86, 0.2f ), ChartColor.FromRgba( 75, 192, 192, 0.2f ), ChartColor.FromRgba( 153, 102, 255, 0.2f ), ChartColor.FromRgba( 255, 159, 64, 0.2f ) };
    List<string> borderColors = new List<string> { ChartColor.FromRgba( 255, 99, 132, 1f ), ChartColor.FromRgba( 54, 162, 235, 1f ), ChartColor.FromRgba( 255, 206, 86, 1f ), ChartColor.FromRgba( 75, 192, 192, 1f ), ChartColor.FromRgba( 153, 102, 255, 1f ), ChartColor.FromRgba( 255, 159, 64, 1f ) };

    List<double?> RandomizeData()
    {
        var r = new Random( DateTime.Now.Millisecond );

        return new List<double?> { r.Next( 3, 20 ) * r.NextDouble(), r.Next( 3, 30 ) * r.NextDouble(), r.Next( 3, 40 ) * r.NextDouble(), r.Next( 3, 50 ) * r.NextDouble(), r.Next( 3, 60 ) * r.NextDouble(), r.Next( 3, 70 ) * r.NextDouble() };
    }
}
```

## API

### Methods

| Method              | Description                              | Return   | Parameters                             |
|---------------------|------------------------------------------|----------|----------------------------------------|
| AddTrendLineOptions | Adds the trendline options to the chart. | Task     | List<ChartTrendlineData> trendlineData |

###### On this page

#### 

## 