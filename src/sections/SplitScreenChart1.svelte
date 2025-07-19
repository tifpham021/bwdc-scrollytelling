<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    let educationDebt = {
        chart: {
        type: 'line',
        height: 500,
        width: 700,
        },
        title: {
        text: 'Education Debt By Race/Ethnicity'
        },
        subtitle: {
        text: 'Source: <a href="https://blackwealthdata.org/explore/assets" target="_blank">blackwealthdata.org</a>'
        },
        xAxis: {
        categories: ['2007', '2010', '2013', '2016', '2019', '2022']
        },
        yAxis: {
        title: {
            text: 'Percent of Households Holding Education Debt'
        }
        },
        plotOptions: {
        line: {
            dataLabels: {
            enabled: true
            },
            enableMouseTracking: true
        }
        },
        series: [
            {
                name: 'Black',
                data: [22.5, 24.1, 31.2, 30.7, 30.2, 35.9],
                color: '#734059'
            },
            {
                name: 'White',
                data: [13.8, 18.9, 18.4, 20.2, 20.0, 19.8],
                color: '#8DA7BE'
            }
        ],
    };

    let moneyHelp = {
    chart: {
        type: 'column',
        height: 500,
        width: 700,
    },
    title: {
        text: 'Percent of 18-28 Year Olds who Received Help Paying...'
    },
    subtitle: {
        text:
            'Source: <a target="_blank" ' +
            'href="https://blackwealthdata.org/explore/assets">blackwealthdata.org</a>'
    },
    xAxis: {
        categories: ['Tuition', 'Rent, Mortgage, or Dormitory',],
        crosshair: true,
        accessibility: {
            description: 'Types of Payments'
        }
    },
    yAxis: {
        min: 0,
        title: {
            text: 'Percentage (%)'
        }
    },
    tooltip: {
        valueSuffix: ' %'
    },
    plotOptions: {
        column: {
            pointPadding: 0.2,
            borderWidth: 0
        }
    },
    series: [
        {
            name: 'Black',
            data: [10.2, 9.9]
        },
        {
            name: 'White',
            data: [14.8, 17.2]
        }
    ]

    }
  </script>
    <div class="background-wrapper">
      <Scroller layout="right">
        {#snippet sticky()}
        <div class="sticky-content-1">
            <Chart {Highcharts} options={educationDebt} />
        </div>
        {/snippet}
  
        {#snippet scrolly()}
        <div class="chart-explanation-1">
            <h3>
                What happened to Cierra and Laura plays out at a much bigger scale. Let's take a 
                moment to explore the data on the left.
            </h3>
        </div>
        <div class="chart-explanation-2">
            <h3>
                Over more than two decades, data shows that Black households 
                consistently carried higher student loan debt compared to White 
                households, with the largest gap reaching 16.1% in 2022.
            </h3>
        </div>
        {/snippet}
      </Scroller>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@300&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/split-screen-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 350vh;
      display: flex;
    }

    .sticky-content-1 {
        height: 50vh;
        position: sticky;
        top: 0;
        align-content: center;
    }

    .sticky-content-2 {
        height: 150vh;
        position: sticky;
        top: 0;
        align-content: center;
    }

    .chart-explanation-1, .chart-explanation-2, .chart-explanation-3 {
        display: flex;
        justify-content: center;
        margin-top: 100vh;
        width: 100%;
        padding: 0 4rem;

    }

    .chart-explanation-2, .chart-explanation-3 {
        display: flex;
        justify-content: center;
        margin-top: 30vh;
        width: 100%;
        padding: 0 4rem;

    }
    
    .chart-explanation-1 h3, .chart-explanation-2 h3, .chart-explanation-3 h3 {
        color: white;
        background-color: #734059;
        padding: 40px 30px;
        max-width: 500px;
        font-size: 1.7em;
        border-radius: 40px;
        text-align: center;
        font-family: 'Inter', serif;
    }

  </style>
  