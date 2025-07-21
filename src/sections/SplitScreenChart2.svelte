<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import debt from "../images/debt.png";
    import debtFree from "../images/debt-free.png";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    import { fade } from 'svelte/transition';
    let visible1 = false;
    let visible2 = false;
    let visible3 = false;

    function inView(node, callback) {
        const observer = new IntersectionObserver(
        ([entry]) => {
            callback(entry.isIntersecting);
        },
        { threshold: 0.5 }
        );

        observer.observe(node);

        return {
        destroy() {
            observer.unobserve(node);
        }
        };
    }

    let moneyHelp = {
    chart: {
        type: 'column',
        height: 500,
        width: 700,
    },
    title: {
        text: '18-28 Year Olds who Received Help Paying...(2021)'
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
      <Scroller layout="left">
        {#snippet sticky()}
        <div class="sticky-content-1"
        use:inView={(val) => (visible1 = val)}
        transition:fade
        class:invisible={!visible1}>
            <Chart {Highcharts} options={moneyHelp} />
        </div>
        {/snippet}
  
        {#snippet scrolly()}
        <div class="chart-explanation-1"
        use:inView={(val) => (visible2 = val)}
        transition:fade
        class:invisible={!visible2}>
            <h3>
                Additionally, <span>White individuals are more likely than Black 
                individuals to receive family financial support for education</span>—leaving 
                many Black students, like Cierra, with no choice but to take out student loans.
            </h3>
        </div>
        <div class="chart-explanation-2"
        use:inView={(val) => (visible3 = val)}
        transition:fade
        class:invisible={!visible3}>
            <h3>
                None of this is coincidental—it <span> deep-rooted inequalities. </span>
                It shows how generational wealth and access significantly affects who 
                takes on debt, shaping careers and futures alike.
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
    }

    .sticky-content-1 {
        height: 100vh;
        position: sticky;
        top: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-1 {
        display: flex;
        justify-content: center;
        margin-top: 100vh;
        width: 100%;
        transition: opacity 0.5s ease-in-out;

    }

    .chart-explanation-2 {
        display: flex;
        justify-content: center;
        width: 100%;
        transition: opacity 0.5s ease-in-out;
    }
    
    .chart-explanation-1 h3, .chart-explanation-2 h3 {
        color: white;
        background-color: #734059;
        padding: 40px 30px;
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

    .invisible {
      opacity: 0;
    }

  </style>
  