<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import house from "../images/house.png";
    import apartment from "../images/apartment.png";

    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    let showCumulative = false;

    let CierraHomeEquity = {
        chart: { zoomType: 'xy', height: 500, width: 700, },
        title: { text: "Cierra’s Rent Costs Over 5 Years" },
        xAxis: { categories: ['Year 0', 'Year 1', 'Year 2', 'Year 3', 'Year 4', 'Year 5'] },
        yAxis: { title: { text: 'Rent Paid ($)' } },
        series: [
        {
            name: 'Annual Rent Paid',
            type: 'column',
            data: [19200, 19968, 20772, 21600, 22464, 23364],
            color: '#90ed7d'
        },
        {
            name: 'Cumulative Rent Paid',
            type: 'area',
            data: [19200, 39168, 59940, 81540, 104004, 127368],
            color: '#7cb5ec',
            visible: showCumulative
        },
    ]
    };

    function showCumulativeRent() {
        showCumulative = true;
        CierraHomeEquity = {
            ...CierraHomeEquity,
            series: CierraHomeEquity.series.map(s => ({
                ...s,
                visible: s.name === 'Cumulative Rent Paid' ? true : true
            }))
        };
    }


  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet sticky()}
      {/snippet}

        {#snippet scrolly()}
            <div class="scrolly1">
                <h3>
                    To understand how renting affected Cierra's 
                    financial picture, let's look at the details 
                    of her rent payments year by year.
                </h3>
                
            </div>
      {/snippet}
    </Scroller>
    <div class="scene3">
        <div class="scrolls">
            <div class="scrolly-text1">
                <p>
                    When Cierra <span>began renting,</span> her annual rent 
                    was <span>$18,000 ($1500 per month). </span>
                </p>
                <p>
                    Each year after that, the <span>rent steadily increased— </span> 
                    adding up quickly with <span>no equity gained in return.</span>
                </p>
            </div>
            <div class="scrolly-text2">
                <p>
                    In five years, Cierra paid <span>a total of $127,368 in rent</span>. 
                    Unlike a mortgage, where monthly payments help build ownership 
                    in a home, every dollar Cierra spent went to her landlord, <span>leaving her 
                    with no equity, asset, or long term wealth to show for it.</span>
                </p>
            </div>
        </div>
            <div class="sticky1">
                <Chart {Highcharts} options={CierraHomeEquity} />
                <button on:click={showCumulativeRent}>Click to see the total rent Cierra paid</button>
            </div>
    </div>
    <div class="summary">
        <h2 class="summary-header">To Summarize...</h2>
        <div class="summary-content">
            <div class="summary-cierra">
                <img src={apartment} alt="4 story red apartment"/>
                <h3>In contrast, Cierra <span>paid $127,368 in rent</span> during the same period, with nothing to show for it—no ownership, no equity, and no lasting financial benefit.</h3>
            </div>
            <div class="summary-laura"> 
                <img src={house} alt="2 story pink house"/>
                <h3>Over five years, Laura <span>built nearly $110,000 in home equity</span>—turning her monthly payments into long-term wealth.</h3>
            </div>
        </div>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 650vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/cierra-apartment-scene.png");
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
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
    }


    .sticky1 {
        display: flex;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
        flex-direction: column;
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

    .summary {
        margin-top: 50vh;
    }

    .summary-header {
        justify-self: center;
        font-family: 'Inter', serif;
        font-weight: 700;
        font-size: 4em;
        margin: 80px;
    }

    .summary-content {
        display: flex;
        justify-content: center;
    }

    .summary-cierra {
        justify-self: center;
        flex-direction: column;
        align-items: center;
        margin: 0 auto;
    }

    .summary-cierra img {
        display: block;
        margin: 0 auto;
        max-width: 100%; 
        height: 55%;
    }

    .summary-laura img {
        height: 50%;
    }

    .summary-laura {
        justify-self: center;
        margin: 0 auto;
    }


    .summary-cierra h3 {
        font-size: 1.5em;
        max-width: 450px;
        text-align: center;
        padding: 50px;
    }

    .summary-laura h3 {
        font-size: 1.5em;
        max-width: 400px;
        text-align: center;
        justify-self: center;
        padding: 50px;
        margin-top: 55px;
    }

  </style>
  