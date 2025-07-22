<script>
    import Scroller from "../lib/Scroller.svelte";
    import cierraCredit from "../images/cierra-credit-score.png";
    import lauraCredit from "../images/laura-credit-score.png";
    import cierraResult from "../images/cierra-result.png";
    import lauraResult from "../images/laura-result.png";

    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;
    let visible5 = false;
    let visible6 = false;
    let visible7 = false;
    let visible8 = false;

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
  </script>
  
  <div class="background-wrapper">
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="office-content1">
                <div class="cierra">
                    <h2 use:inView={(val) => (visible1 = val)}
                        transition:fade
                        class:invisible={!visible1}>Cierra</h2>
                    <div class="text" use:inView={(val) => (visible2 = val)}
                        transition:fade
                        class:invisible={!visible2}>
                        <h3><span>1.</span> Took out <span>significant student loans</span> throughout college</h3>
                        <h3><span>2.</span> <span>Will not receive any financial help</span> from her family— including for a down payment</h3>
                    </div>
                </div>
                <div class="laura">
                    <h2 use:inView={(val) => (visible1 = val)}
                        transition:fade
                        class:invisible={!visible1}>Laura</h2>
                    <div class="text" use:inView={(val) => (visible2 = val)}
                        transition:fade
                        class:invisible={!visible2}>
                        <h3><span>1.</span> Took out a <span>few student loans,</span> but was able to repay them by graduation</h3>
                        <h3><span>2.</span> Her parents are <span>gifting her a down payment</span> to help with her first home</h3>
                    </div>
                </div>
            </div>
            <div class="office-content2">
                <h3 use:inView={(val) => (visible3 = val)}
                    transition:fade
                    class:invisible={!visible3}>
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
                <div class="sticky-content" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    <div class="cierra">
                        <img src={cierraCredit} alt="credit report of 670"/>
                    </div>
                </div>
                <div class="scroll-text-cierra" use:inView={(val) => (visible5 = val)}
                    transition:fade
                    class:invisible={!visible5}>
                    <p>
                        While Cierra’s <span>credit score is decent,</span> it falls just 
                        <span>below the threshold </span> for most conventional mortgage 
                        approvals— especially with her high student debt and lack of savings.
                        <br><br> <span>She’s eligible for only a limited number of loan options</span>—usually 
                        with higher interest rates.
                    </p>
                </div>
            </div>
            <div class="credit-column">
                <div class="sticky-content" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    <div class="laura">
                        <img src={lauraCredit} alt="credit report of 760"/>
                    </div>
                </div>
                <div class="scroll-text-laura" use:inView={(val) => (visible5 = val)}
                    transition:fade
                    class:invisible={!visible5}>
                    <p>
                        Laura’s <span>credit score is excellent </span> due to her low debt, 
                        strong financial supports and timely repayments.<br><br> She’s eligible 
                        for the best mortgage rates and <span>will be quickly be pre-approved.</span>
                    </p>
                </div>
            </div>
        </div>
        <div class="office-content3">
            <h3 use:inView={(val) => (visible6 = val)}
                transition:fade
                class:invisible={!visible6}>
                Due to their credit scores, they received different outcomes when they applied for 
                their mortgages in Atlanta.
            </h3>
        </div>
        <div class="scroll-wrapper">
            <div class="results">
                <div class="result-column">
                    <div class="sticky-content-result">
                        <div class="cierra">
                            <img src={cierraResult} alt="clipboard with an application that was denied" use:inView={(val) => (visible7 = val)}
                            transition:fade
                            class:invisible={!visible7}/>
                        </div>
                    </div>
                    <div class="scroll-result-cierra">
                        <p use:inView={(val) => (visible8 = val)}
                            transition:fade
                            class:invisible={!visible8}>
                            DENIED
                        </p>
                    </div>
                </div>
                <div class="result-column">
                    <div class="sticky-content-result" >
                        <div class="laura">
                            <img src={lauraResult} alt="clipboard with an application that was approved" use:inView={(val) => (visible7 = val)}
                            transition:fade
                            class:invisible={!visible7}/>
                        </div>
                    </div>
                    <div class="scroll-result-laura">
                        <p use:inView={(val) => (visible8 = val)}
                            transition:fade
                            class:invisible={!visible8}>
                            APPROVED
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@300&display=swap");
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
        transition: opacity 0.5s ease-in-out;
    }

    .text {
        display: flex;
        flex-direction: column;
        background-color: #D3EBF4;
        max-width: 360px;
        font-size: 1.8em;
        padding: 35px 55px;
        border-radius: 80px;
        display: flex;
        align-self: center;
        color: black;
        text-align: center;
        transition: opacity 0.5s ease-in-out;
        gap: 20px;
    }

    .text h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
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
        font-family: 'Inter', serif;
        font-weight: 300;
        max-width: 400px;
        padding: 100px;
        font-size: 2.2em;
        justify-self: center;
        transition: opacity 0.5s ease-in-out;
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
        transition: opacity 0.5s ease-in-out;
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
        transition: opacity 0.5s ease-in-out;
    }

    .scroll-text-laura {
        display: flex;
        flex-direction: column;
    }

    .invisible {
      opacity: 0;
    }

    .scroll-text-cierra p, .scroll-text-laura p {
        color: black;
        font-family: 'Inter', serif;
        font-weight: 300;
        font-size: 1.6em;
        max-width: 450px;
        justify-self: center;
        text-align: center;
        padding: 30px 10px;
    }

    .credit-column {
        display: flex;
        flex-direction: column;
        margin: 0 auto;
    }

    .credit-stuff {
        display: flex;
        justify-content: center;
    }

    /* Transition scene */
    .office-content3 {
        margin-top: 70vh;
        justify-self: center;
    }

    .office-content3 h3 {
        color: white;
        background-color: #4583A2;
        border-radius: 90px;
        text-align: center;
        font-family: 'Inter', serif;
        font-weight: 300;
        max-width: 500px;
        padding: 70px 60px;
        font-size: 2.2em;
        justify-self: center;
        transition: opacity 0.5s ease-in-out;
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
        display: flex;
        flex-direction: column;
        height: 200vh;
    }

    .scroll-result-cierra p {
        background-color: #EA7D7D;
        text-align: center;
        font-family: 'Anonymous Pro', serif;
        font-size: 2.5em;
        padding: 20px;
        width: 400px;
        border-radius: 40px;
        transform: translateX(15%);
        transition: opacity 0.5s ease-in-out;
    }

    .scroll-result-laura p {
        background-color: #C4F1A6;
        text-align: center;
        font-family: 'Anonymous Pro', serif;
        font-size: 2.5em;
        padding: 20px;
        width: 400px;
        border-radius: 40px;
        margin: 0 0 0 -20px;
        transition: opacity 0.5s ease-in-out;
    }

    .sticky-content-result {
        display: flex;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
        transition: opacity 0.5s ease-in-out;
    }

    .result-column {
        margin: 0 auto;
    }

    .scroll-wrapper {
        height: 300vh;
        position: relative;
    }

    .laura img, .cierra img{
        transition: opacity 0.5s ease-in-out;
    }

  </style>
  