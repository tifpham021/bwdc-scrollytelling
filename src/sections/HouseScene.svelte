<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import house from "../images/house.png";
    import apartment from "../images/apartment.png";

    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';
    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;
    let visible5 = false;
    let visible6 = false;

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

    let showCumulative = false;

    let lauraHomeEquity = {
        chart: {
        zoomType: 'xy',
        width: 700,
        height: 500
    },
        title: {
            text: 'Laura’s Home Equity Growth Over 5 Years'
        },
        xAxis: {
            categories: ['Year 0', 'Year 1', 'Year 2', 'Year 3', 'Year 4', 'Year 5']
        },
        yAxis: [{
            title: { text: 'Amount ($)' }
        }],
        plotOptions: {
            column: { stacking: 'normal' }
        },
        series: [
            {
                type: 'column',
                name: 'Appreciation Gain',
                data: [0, 14000, 14560, 15142, 15748, 16378],
                color: '#7cb5ec'
            },
            {
                type: 'column',
                name: 'Principal Paid',
                data: [0, 5000, 6000, 7000, 8000, 9000],
                color: '#90ed7d'
            },
            {
                type: 'line',
                name: 'Total Equity',
                data: [35000, 54000, 74560, 96702, 120450, 145828],
                color: '#434348',
                marker: { enabled: true },
                visible: false
            }
        ]
    };

    function showCumulativeEquity() {
        showCumulative = true;
        lauraHomeEquity = {
            ...lauraHomeEquity,
            series: lauraHomeEquity.series.map(s => ({
                ...s,
                visible: s.name === 'Total Equity' ? true : true
            }))
        };
    }
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet sticky()}
      {/snippet}

        {#snippet scrolly()}
            <div class="scrolly1" use:inView={(val) => (visible1 = val)}
                transition:fade
                class:invisible={!visible1}>
                <h3>
                    Let’s see how buying a home helped 
                    Laura grow her wealth over five years.
                </h3>
                <img src={house} alt="2 story magenta house"/>
            </div>
            <div class="scrolly2" use:inView={(val) => (visible2 = val)}
                transition:fade
                class:invisible={!visible2}>
                <h3>
                    To understand how that growth happened, here are
                    the details of her home purchase—what 
                    she paid up front, how much equity she gained, 
                    and how the value of her home changed over time.
                </h3>
            </div>
      {/snippet}
    </Scroller>
    <div class="scene3">
        <div class="scrolls">
            <div class="scrolly-text1" use:inView={(val) => (visible4 = val)}
                transition:fade
                class:invisible={!visible4}>
                <p>
                    <span>Purchase price:</span> $350,000
                </p>
                <p>
                    <span>Down payment:</span> 10% ($35,000)
                </p>
                <p>
                    <span>Loan amount:</span> $315,000
                </p>
                <p>
                    <span>Interest rate:</span> 6% (30-year fixed mortgage)
                </p>
                <p>
                    <span>Annual home appreciation:</span> 4% 
                </p>
            </div>
            <div class="scrolly-text2" use:inView={(val) => (visible5 = val)}
                transition:fade
                class:invisible={!visible5}>
                <p>In five years, Laura’s home <span>grew in value by over $75,000.</span> 
                    She also paid down about $35,000 of her loan. Together, her 
                    equity rose from $35,000 to nearly $146,000 — a <span>$110,000 gain 
                    in wealth from homeownership.</span></p>
            </div>
        </div>
            <div class="sticky1" use:inView={(val) => (visible3 = val)}
                transition:fade
                class:invisible={!visible3}>
                <Chart {Highcharts} options={lauraHomeEquity} />
                <button on:click={showCumulativeEquity}>Click to see the total home equity Laura earned</button>
            </div>
    </div>
    <div class="scene4" use:inView={(val) => (visible6 = val)}
        transition:fade
        class:invisible={!visible6}>
        <img src={apartment} alt="4 story red apartment"/>
        <h3>
            While Laura’s wealth grew through homeownership, let’s see how renting 
            affected Cierra’s finances over those same five years.
        </h3>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 750vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/laura-house-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #4A6499;
        color: white;
        max-width: 650px;
        font-size: 2em;
        text-align: center;
        padding: 50px;
        border-radius: 90px;
        align-self: center;
    }

    .scrolly1 {
        display: flex;
        align-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .scrolly2 {
        margin-top: 90vh;
        align-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .scene3 {
        margin-top: 90vh;
        text-align: center;
        justify-content: space-between;
        height: 240vh;
        display: flex;
        margin: 3%;
    }

    .scrolly-text1 {
        align-self: center;
        background-color: #2f4776;
        color: white;
        font-family: 'Inter', serif;
        font-weight: 300;
        padding: 40px;
        font-size: 1.6em;
        border-radius: 80px;
        max-width: 550px;
        margin-top: 100vh;
        z-index: 10;
        position: relative;
        transition: opacity 0.5s ease-in-out;
    }

    .scrolly-text2 {
        align-self: center;
        background-color: #2f4776;
        color: white;
        font-family: 'Inter', serif;
        font-weight: 300;
        padding: 40px;
        font-size: 1.6em;
        border-radius: 80px;
        max-width: 550px;
        margin-top: 30vh;
        z-index: 10;
        position: relative;
        transition: opacity 0.5s ease-in-out;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 500;
        font-size: 1em;
    }

    .sticky1 {
        display: flex;
        flex-direction: column;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
        transition: opacity 0.5s ease-in-out;
    }

    .scene4 {
        display: flex;
        justify-content: center;
        margin-top: 70vh;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    button {
        background-color: rgb(101, 162, 211);
        border: none;
        padding: 30px;
        border-radius: 40px;
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1.5em;
        box-shadow: 1px 3px 2px rgb(66, 107, 141);
        margin: 20px;
        color: white;
    }

    button:hover {
        transform: translateY(2px);
        box-shadow: 1px 4px 4px rgb(51, 84, 111);
    }

    button:active {
        transform: scale(0.98);
        box-shadow: 1px 3px 2px rgb(49, 80, 106);
    }


  </style>
  