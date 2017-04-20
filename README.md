# Build React Timeseries Charts

Current features include:

 * Declarative layout of charts using JSX
 * Interactivity, including pan and zoom
 * Add new chart types or overlays
 * Multiple axis, multiple rows
 * Line, area, scatter, bar and boxplot charts
 * Brushing
 * Legends
 * Overlay markers

Getting started
---------------

install:

    npm install react-timeseries-charts pondjs --save

Once installed, you can import the necessary components from the library:

    import { Charts, ChartContainer, ChartRow, YAxis, LineChart } from "react-timeseries-charts";

Then we construct our chart in the `render()` function of our component. For a simple example we create a chart with two line charts on it, specified in JSX:

    <ChartContainer timeRange={series1.timerange()} width={800}>
        <ChartRow height="200">
            <YAxis id="axis1" label="AUD" min={0.5} max={1.5} width="60" type="linear" format="$,.2f"/>
            <Charts>
                <LineChart axis="axis1" series={series1}/>
                <LineChart axis="axis2" series={series2}/>
            </Charts>
            <YAxis id="axis2" label="Euro" min={0.5} max={1.5} width="80" type="linear" format="$,.2f"/>
        </ChartRow>
    </ChartContainer>

Data format
-----------

    import { TimeSeries, TimeRange } from "pondjs";

    const data = {
        name: "traffic",
        columns: ["time", "in", "out"],
        points: [
            [1400425947000, 52, 41],
            [1400425948000, 18, 45],
            [1400425949000, 26, 49],
            [1400425950000, 93, 81],
            ...
        ]
    };

    const timeseries = new TimeSeries(data);

    var timerange = timeseries.timerange()

    var timerange = new TimeRange([begin, end]);

Developing
----------

The repo contains the examples website. This is very helpful in developing new functionality. Within a cloned repo, you first need to run:

    npm install

This will install the development dependencies into your node_modules directory.

You can then start up the test server:

    npm run start-website

Then, point your browser to:

[http://localhost:3000/](http://localhost:3000/)
