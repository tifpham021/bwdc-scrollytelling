<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';
    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;
    let visible5 = false;

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

    let mortgages = {
        chart: {
        type: 'column',
        width: 700,
        height: 600
    },
    title: {
        text: 'Loan Actions Taken by Race/ Ethnicity'
    },
    subtitle: {
        text:
            'Source: <a target="_blank" ' +
            'href="https://blackwealthdata.org/explore/homeownership">blackwealthdata.org</a>'
    },
    xAxis: {
        categories: ['Denied', 'Approved'],
        crosshair: true,
        accessibility: {
            description: 'Races/ Ethnicities'
        }
    },
    yAxis: {
        min: 0,
        title: {
            text: 'Actions Taken per 100 People'
        }
    },
    tooltip: {
        valueSuffix: ''
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
            data: [0.65, 0.99]
        },
        {
            name: 'White',
            data: [0.49, 1.73]
        }
    ]
};
  </script>
    <div class="background-wrapper">
        <div class="top">
            <Scroller layout="right">
                {#snippet sticky()}
                <div class="sticky-content-1" use:inView={(val) => (visible1 = val)}
                    transition:fade
                    class:invisible={!visible1}>
                    <Chart {Highcharts} options={mortgages} />
                </div>
                {/snippet}
        
                {#snippet scrolly()}
                <div class="chart-explanation-1" use:inView={(val) => (visible2 = val)}
                    transition:fade
                    class:invisible={!visible2}>
                    <h3>
                        Out of every 100 mortgage applicants, <span>0.65 Black individuals</span> are 
                        denied— compared to just <span>0.49 White individuals.</span>

                    </h3>
                </div>
                <div class="chart-explanation-2" use:inView={(val) => (visible3 = val)}
                    transition:fade
                    class:invisible={!visible3}>
                    <h3>
                        That may seem small at first, but it represents a nearly <span>33% higher 
                        denial rate </span> for Black applicants.
                    </h3>
                </div>
                <div class="chart-explanation-3" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    <h3>
                        The approval gap is even more striking: White applicants are <span> approved 
                        at a rate 75% higher</span> than Black applicants.
                    </h3>
                </div>
                {/snippet}
            </Scroller>
        </div>
        <div class="chart-explanation-4" use:inView={(val) => (visible5 = val)}
            transition:fade
            class:invisible={!visible5}>
            <h3>
                Given the earlier data showing that <span>Black individuals earn less income and carry higher 
                student debt than White individuals,</span> these financial disparities likely contribute to the 
                <span>significantly lower mortgage approval rates and higher denial rates</span> seen among Black applicants. 
                Access to homeownership is deeply tied to financial standing — and <span>these systemic inequalities create real barriers.</span>
            </h3>
        </div>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/office4-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 700vh;
      display: flex;
      flex-direction: column;
    }

    .top {
        display: flex;
        flex-direction: row;
        height: 530vh;
    }

    .sticky-content-1 {
        height: 600vh;
        position: sticky;
        top: 0;
        align-content: center;
        margin-left: 40px;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-1 {
        display: flex;
        justify-content: center;
        margin-top: 100vh;
        width: 100%;
        padding: 0 5rem;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-2 {
        display: flex;
        justify-content: center;
        margin-top: 80vh;
        width: 100%;
        padding: 0 5rem;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-3 {
        display: flex;
        justify-content: center;
        margin-top: 80vh;
        width: 100%;
        padding: 0 5rem;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-4 {
        display: flex;
        justify-content: center;
        margin-top: 20vh;
        transition: opacity 0.5s ease-in-out;
    }

    .chart-explanation-4 h3 {
        color: white;
        background-color: #4583A2;
        border-radius: 30%;
        text-align: center;
        font-family: 'Inter', serif;
        font-weight: 300;
        max-width: 650px;
        padding: 90px;
        font-size: 1.8em;
        justify-self: center;
    }

    
    .chart-explanation-1 h3, .chart-explanation-2 h3, .chart-explanation-3 h3 {
        color: white;
        background-color: #1C1C6E;
        padding: 60px 30px;
        max-width: 400px;
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
  