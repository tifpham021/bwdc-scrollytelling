<script>
    import Scroller from "../lib/Scroller.svelte";
    import cierraCredit from "../images/cierra-credit-score.png";
    import lauraCredit from "../images/laura-credit-score.png";
    import cierraResult from "../images/cierra-result.png";
    import lauraResult from "../images/laura-result.png";
  </script>
  
  <div class="background-wrapper">
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="office-content1">
                <div class="cierra">
                    <h2>Cierra</h2>
                    <div class="text">
                        <h3><span>1.</span> Took out significant student loans throughout college</h3>
                        <h3><span>2.</span> Will not receive any financial help from her family— including for a down payment</h3>
                    </div>
                </div>
                <div class="laura">
                    <h2>Laura</h2>
                    <div class="text">
                        <h3><span>1.</span> Took out a few student loans, but was able to repay them by graduation</h3>
                        <h3><span>2.</span> Her parents are gifting her a down payment to help with her first home</h3>
                    </div>
                </div>
            </div>
            <div class="office-content2">
                <h3>
                    Let’s see how these factors 
                    impacted their credit scores— 
                    and what that meant when it came 
                    time to apply for a mortgage
                </h3>
            </div>
        {/snippet}
        </Scroller>
        <div class="credit-stuff">
            <div class="credit-column">
                <div class="sticky-content">
                    <div class="cierra">
                        <img src={cierraCredit} alt="credit report of 670"/>
                    </div>
                </div>
                <div class="scroll-text-cierra">
                    <p>While Cierra’s <span>credit score is decent,</span> it falls just <span>below the threshold </span> for most conventional mortgage approvals— especially with her high student debt and lack of savings.

                    </p>
                </div>
            </div>
            <div class="credit-column">
                <div class="sticky-content">
                    <div class="laura">
                        <img src={lauraCredit} alt="credit report of 760"/>
                    </div>
                </div>
                <div class="scroll-text-laura">
                    <p>Laura’s <span>credit score is excellent </span> due to her low debt, strong financial supports and timely repayments. </p>
                    <p> She’s eligible for the best mortgage rates and <span>will be quickly be pre-approved.</span></p>
                </div>
            </div>
        </div>
        <div class="office-content3">
            <h3>
                Due to their credit scores, they received different outcomes when they applied for 
                their mortgages in Atlanta.
            </h3>
        </div>
        <div class="results">
            <div class="result-column">
                <div class="sticky-content-result">
                    <div class="cierra">
                        <img src={cierraResult} alt="clipboard with an application that was denied"/>
                    </div>
                </div>
                <div class="scroll-result-cierra">
                    <p>
                        DENIED
                    </p>
                </div>
            </div>
            <div class="result-column">
                <div class="sticky-content-result">
                    <div class="laura">
                        <img src={lauraResult} alt="clipboard with an application that was approved"/>
                    </div>
                </div>
                <div class="scroll-result-laura">
                    <p>
                        APPROVED
                    </p>
                </div>
            </div>
        </div>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@100&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Anonymous+Pro:wght@700&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 1100vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/office3-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    .office-content1 {
        display: flex;
        justify-content: center;
        gap: 20%;
    }

    h2 {
        text-align: center;
        color: white;
        font-family: 'Satisfy', serif;
        font-size: 5em;
    }

    .text {
        display: flex;
        flex-direction: column;
        font-family: 'Tenor Sans', serif;
        font-weight: 400;
        background-color: #D3EBF4;
        max-width: 360px;
        font-size: 1.8em;
        padding: 20px 55px;
        border-radius: 80px;
        display: flex;
        align-self: center;
        color: black;
        text-align: center;
    }

    span {
        font-family: 'Teachers', sans-serif;
        font-size: 1.2em;
    }

    .office-content2 {
        margin-top: 100vh;
        justify-self: center;
    }


    .office-content2 h3 {
        color: white;
        background-color: #4583A2;
        border-radius: 50%;
        text-align: center;
        font-family: 'Tenor Sans', serif;
        max-width: 400px;
        padding: 100px;
        font-size: 2.2em;
        justify-self: center;
    }

    /* Scene of credit scores */

    .sticky-content {
        display: flex;
        height: 60vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
    }


    .scroll-text-cierra, .scroll-text-laura{
        margin-top: 120vh;
        text-align: center;
        background-color: #D3EBF4;
        border-radius: 30px;
        position: relative;
        z-index: 10;
        justify-content: center;
        margin-left: auto;
        margin-right: auto;
        padding: 20px;
    }

    .scroll-text-laura {
        display: flex;
        flex-direction: column;
    }

    .scroll-text-cierra p, .scroll-text-laura p {
        color: black;
        font-family: 'Inter', serif;
        font-size: 1.5em;
        max-width: 450px;
        justify-self: center;
        text-align: center;
    }

    .credit-column {
        display: flex;
        flex-direction: column;
    }

    .credit-stuff {
        display: flex;
    }

    /* Transition scene */
    .office-content3 {
        margin-top: 70vh;
        justify-self: center;
    }

    .office-content3 h3 {
        color: white;
        background-color: #4583A2;
        border-radius: 60px;
        text-align: center;
        font-family: 'Tenor Sans', serif;
        max-width: 500px;
        padding: 40px;
        font-size: 2.2em;
        justify-self: center;
    }

    /* Scene of the mortgage results */

    .results {
        display: flex;
        margin-top: 90vh;
        justify-content: center;
    }

    .results img {
        height: 750px;
    }

    .scroll-result-cierra, .scroll-result-laura {
        text-align: center;
        position: relative;
        z-index: 10;
        justify-content: center;
        margin-left: auto;
        margin-right: auto;
        display: flex;
        flex-direction: column;
        margin-top: 10vh;
    }

    .scroll-result-cierra p {
        background-color: #EA7D7D;
        text-align: center;
        font-family: 'Anonymous Pro', serif;
        font-size: 2.5em;
        padding: 20px;
        width: 350px;
        border-radius: 40px;
        margin: 0 auto;
    }

    .scroll-result-laura p {
        background-color: #C4F1A6;
        text-align: center;
        font-family: 'Anonymous Pro', serif;
        font-size: 2.5em;
        padding: 20px;
        width: 400px;
        border-radius: 40px;
        margin: 0 auto;
    }

    .sticky-content-result {
        display: flex;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
    }

    .result-column {
        margin: 0 auto;
    }

  </style>
  