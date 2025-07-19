<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import debt from "../images/debt.png";
    import debtFree from "../images/debt-free.png";
    
    import Chart from '@highcharts/svelte';
    import Highcharts from 'highcharts';

    let chartOptions = {
        chart: {
        type: 'line'
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
  </script>
    <div class="background-wrapper">
        <div class="person-column">
            <div class="sticky-content">
                <div class="cierra">
                    <h2>Cierra</h2>
                    <img src={debt} alt="shows that person is running out of time to pay their debts with an hourglass and a chart"/>
                </div>
            </div>
            <div class="scroll-text-cierra">
                <p>Cierra graduated with over $30,000 in student loans and no financial help from family.</p>
                <p>She had to begin repaying her loans immediately after graduation.</p>
                <p>This financial pressure shaped her job choices.</p>
            </div>
        </div>
      <Scroller layout="center">
        {#snippet sticky()}
        {/snippet}
  
        {#snippet scrolly()}
        <div class="scrolly-content-1">
            <h3>
                From now on, their journeys will look entirely different— shaped not by effort 
                or ambition, but by systems they never controlled.
            </h3>
        </div>
        {/snippet}
      </Scroller>
        <div class="person-column">
            <div class="sticky-content">
                <div class="laura">
                    <h2>Laura</h2>
                    <img src={debtFree} alt="shows that person debt free"/>
                </div>
            </div>
            <div class="scroll-text-laura">
                <p>Laura graduated debt-free with help from her family.</p>
                <p>She had more freedom to explore job opportunities.</p>
                <p>She could afford to take lower-paying internships.</p>
            </div>
        </div>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/split-screen-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 350vh;
      display: flex;
      justify-content: center;
      grid-template-columns: 1fr 1fr 1fr;
    }

    .sticky-content {
        display: flex;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
    }

    .sticky-content h2 {
        color: white;
        text-align: center;
        font-family: 'Satisfy', serif;
        font-size: 5.5em;
    }

    .scrolly-content-1 {
        margin-top: 30vh;
        color: white;
        font-family: 'Inter', serif;
        text-align: center;
        background-color: #734059;
        font-size: 1.7em;
        border-radius: 80px;
        max-width: 450px;
        padding: 20px 40px;
        position: relative;
    }

    .cierra {
        margin-top: -35%;
        justify-content: center;
        align-content: center;
        margin-right: -35%;
    }

    .scroll-text-cierra {
        transform: translateX(20%);
    }

    .cierra img, .laura img {
        margin-top: -30px;
    }

    .laura {
        margin-top: -35%;
        margin-left: -35%;
    }

    .scroll-text-laura {
        transform: translateX(-18%);
    }

    .laura img {
        width: 380px;
    }

    .scroll-text-cierra, .scroll-text-laura{
        margin-top: 140vh;
        text-align: center;
        background-color: #DD9EBC;
        border-radius: 50px;
        position: relative;
        z-index: 10;
        padding: 20px;
    }

    .scroll-text-cierra p, .scroll-text-laura p {
        color: black;
        font-family: 'Inter', serif;
        font-size: 1.5em;
        max-width: 400px;
        justify-self: center;
    }

    .person-column {
        display: flex;
        flex-direction: column;
    }

    

  </style>
  