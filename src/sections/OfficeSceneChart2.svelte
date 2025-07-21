<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import debt from "../images/debt.png";
    import debtFree from "../images/debt-free.png";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    let medianIncome = {
        chart: {
        type: 'bar',
        height: 600,
    },
    title: {
        text: 'Median Earnings (Ages 25–34, Bachelor’s)'
    },
    subtitle: {
        text: 'Source: <a ' +
            'href="https://blackwealthdata.org/explore/employment"' +
            'target="_blank">blackwealthdata.org</a>'
    },
    xAxis: {
        categories: ['2010', '2014', '2018', '2022'],
        title: {
            text: null
        },
        gridLineWidth: 1,
        lineWidth: 0
    },
    yAxis: {
        min: 0,
        title: {
            text: 'Median Annual Earnings',
            align: 'high'
        },
        labels: {
            overflow: 'justify'
        },
        gridLineWidth: 0
    },
    tooltip: {
        valueSuffix: ' thousand'
    },
    plotOptions: {
        bar: {
            borderRadius: '50%',
            dataLabels: {
                enabled: true
            },
            groupPadding: 0.1
        }
    },
    legend: {
        layout: 'vertical',
        align: 'right',
        verticalAlign: 'top',
        x: -40,
        y: 80,
        floating: true,
        borderWidth: 1,
        backgroundColor: 'var(--highcharts-background-color, #ffffff)',
        shadow: true
    },
    credits: {
        enabled: false
    },
    series: [{
        name: 'White',
        data: [62960, 63110, 67530, 70250]
    }, {
        name: 'Black',
        data: [51980, 58000, 49070, 56030]
    }]
    }
  </script>
    <div class="background-wrapper">
      <Scroller layout="left">
        {#snippet sticky()}
        <div class="sticky-content-1">
            <Chart {Highcharts} options={medianIncome} />
        </div>
        {/snippet}
  
        {#snippet scrolly()}
        <div class="scrolly-content">
            <div class="chart-explanation-1">
                <h3>
                    From 2010 to 2022, <span>White individuals 
                    consistently earned higher annual salaries 
                    than Black individuals</span>—even when <span>both held 
                    a Bachelor's degree.</span>
                </h3>
            </div>
            <div class="chart-explanation-2">
                <h3>
                    The <span>median annual income gap</span> between White and Black 
                    workers ranged from <span>$5,110</span> to <span>$18,460</span>
                    —year after year.
                </h3>
            </div>
            <div class="chart-explanation-3">
                <h3>
                    <span>Think back to the comparison between Cierra and Laura: </span>
                    we’ve already seen how quickly these earnings gaps can 
                    compound over time.
                </h3>
            </div>
            <div class="chart-explanation-4">
                <h3>
                    <span>Family wealth, student debt, and now income inequality</span>—all 
                    of these factors combine to <span>deepen the racial wealth gap across 
                    generations.</span>
                </h3>
            </div>
        </div>
        {/snippet}
      </Scroller>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@300&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/office-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 550vh;
    }

    .sticky-content-1 {
        height: 100vh;
        position: sticky;
        top: 0;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .chart-explanation-1 {
        display: flex;
        justify-content: center;
        margin-top: 100vh;
        width: 100%;
    }

    .scrolly-content {
        position: relative;
        z-index: 2;
        height: 430vh;
    }

    .chart-explanation-2 {
        display: flex;
        justify-content: center;
        width: 100%;
        margin-top: 50vh;
    }

    .chart-explanation-3 {
        display: flex;
        justify-content: center;
        width: 100%;
        margin-top: 50vh;
    }

    .chart-explanation-4 {
        display: flex;
        justify-content: center;
        width: 100%;
        margin-top: 50vh;
    }
    
    .chart-explanation-1 h3, .chart-explanation-2 h3, .chart-explanation-3 h3, .chart-explanation-4 h3 {
        color: white;
        background-color: #1C1C6E;
        padding: 50px 40px;
        max-width: 500px;
        font-size: 1.7em;
        border-radius: 70px;
        text-align: center;
        font-family: 'Inter', serif;
        font-weight: 300;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
    }

  </style>
  