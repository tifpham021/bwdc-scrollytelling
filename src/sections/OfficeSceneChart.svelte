<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    let income = {
        chart: {
        type: 'line',
        height: 600,
        width: 700,
        },
        title: {
        text: 'Total Income Over the Span of 5 Years'
        },
        subtitle: {
        text: 'Source: <a href="https://blackwealthdata.org/explore/assets" target="_blank">blackwealthdata.org</a>'
        },
        xAxis: {
        categories: ['1', '2', '3', '4', '5']
        },
        yAxis: {
        title: {
            text: 'Amount of Money (Thousands)'
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
                name: 'Cierra',
                data: [60, 120, 180, 240, 300],
                color: '#734059'
            },
            {
                name: 'Laura',
                data: [72, 144, 216, 288, 360],
                color: '#8DA7BE'
            }
        ],
    };
  </script>
    <div class="background-wrapper">
      <Scroller layout="right">
        {#snippet sticky()}
        <div class="sticky-content-1">
            <Chart {Highcharts} options={income} />
        </div>
        {/snippet}
  
        {#snippet scrolly()}
        <div class="chart-text">
            <div class="chart-explanation-1">
                <h3>
                    What started as only <span>$12,000</span>, 
                    quickly turned into a wealth gap of <span>$60,000.</span>
                </h3>
            </div>
            <div class="chart-explanation-2">
                <h3>
                    Laura and Cierra's story isn't unique. <span>Across the entire country, racial income gaps persist</span> 
                    and are much more common than we think.
                </h3>
            </div>
        </div>
        {/snippet}
      </Scroller>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@300&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/office-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 400vh;
      display: flex;
      justify-content: center;
    }

    .sticky-content-1 {
        height: 150vh;
        position: sticky;
        top: 0;
        align-content: center;
        margin: 0 auto;
    }

    .chart-text {
        margin: 0 auto;
    }

    .chart-explanation-1 {
        display: flex;
        justify-content: center;
        margin-top: 100vh;
        width: 100%;
        padding: 0 2rem;

    }

    .chart-explanation-2 {
        display: flex;
        justify-content: center;
        margin-top: 90vh;
        width: 100%;
        padding: 0 2rem;

    }

    
    .chart-explanation-1 h3, .chart-explanation-2 h3 {
        color: white;
        background-color: #1C1C6E;
        padding: 60px 30px;
        max-width: 390px;
        font-size: 1.8em;
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
  