<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import cierraIcon from "../images/cierra-smiling.png";
    import lauraIcon from "../images/laura1.png";
    import cierraCheck from "../images/cierraCheck.png";
    import lauraCheck from "../images/lauraCheck.png";
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet scrolly()}
        <h3>Debt wasn’t the only difference. 
            When they entered the workforce, 
            inequality followed them through the door.
        </h3>
        <div class="scene2">
            <div class="images">
                <img src={cierraIcon} alt="icon of smiling woman with brown hair" class="cierra-icon"/>
                <img src={cierraCheck} alt="check of 60k" class="check"/>
            </div>
                <h4>Cierra's annual salary is <span class="amount">$60,000.</span></h4>
        </div>
        <div class="scene3">
            <div class="images">
                <img src={lauraCheck} alt="check of 72k" class="check"/>
                <img src={lauraIcon} alt="icon of smiling woman with blonde hair" class="laura-icon"/>
            </div>
                <h4>Laura's annual salary is <span class="amount">$72,000.</span>.</h4>
        </div>
        <div class="scene4">
            <h2>Laura makes <span class="amount">$12,000</span> more than Cierra every year.</h2>
        </div>
        <div class="scene5">
            <h2>That may not seem like much of a difference, but it adds up over time.</h2>
        </div>
      {/snippet}

      {#snippet sticky()}
      {/snippet}

    
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 620vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/office-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Tenor Sans', serif;
        background-color: #1C1C6E;
        color: white;
        max-width: 650px;
        font-size: 2.3em;
        text-align: center;
        padding: 40px 45px;
        border-radius: 120px;
        display: flex;
        align-self: center;
    }

    .scene2, .scene3 {
        margin-top: 50vh;
    }

    .scene4 {
        margin-top: 50vh;
    }

    .scene5 {
        margin-top: 60vh;
    }

    .scene6 {
        margin-top: 100vh;
        position: relative;
    }

    
    .images {
        display: flex;
        justify-content: center;
        gap: 40px;
    }

    h4, h2 {
        background-color: #1C1C6E;
        color: white;
        text-align: center;
        font-family: 'Tenor Sans', serif;
        font-size: 2em;
        max-width: 700px;
        justify-self: center;
        padding: 30px 40px;
        border-radius: 50px;
        margin-top: 7%;
    }

    .amount {
        font-family: 'Teachers', serif;
    }

    .cierra-icon {
        height: 365px;
    }

    .check {
        height: 360px;
    }

    .laura-icon {
        height: 400px;
    }

    .sticky-content {
        margin-top: 80vh;
        position: sticky;
        top: 0;
        align-content: center;
    }

  </style>
  