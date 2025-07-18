<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import leftHouse from "../images/leftHouse.png";
    import rightHouse from "../images/rightHouse.png";
    import leftSign from "../images/leftSign.png";
    import rightSign from "../images/rightSign.png";

  </script>
  
  <div class="background-wrapper">
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="goal-content">
                <h3>They both have the goal of owning a house by 30.</h3>
                <div class="houses">
                    <div class="left">
                        <img src={leftHouse} alt="two story pink house"/>
                        <img src={leftSign} alt="purple sold sign"/>
                    </div>
                    <div class="right">
                        <img src={rightSign} alt="blue sold sign"/>
                        <img src={rightHouse} alt="one story pink house with blue roof"/>
                    </div>
                </div>
            </div>
        {/snippet}
        </Scroller>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=The+Nautigal:wght@700&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 180vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/goal-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h1 {
        background-color: #C1C0DF;
        font-family: 'The Nautigal';
        text-align: center;
        font-size: 5.8em;
        max-width: 400px;
        border-radius: 30px;
        padding: 5px 60px;
        display: flex;
        justify-self: center;
        margin-top: -25%;
    }

    h3 {
        font-family: 'Tenor Sans', serif;
        background-color: #FCEFAF;
        max-width: 420px;
        font-size: 2.6em;
        text-align: center;
        padding: 30px 35px;
        border-radius: 40px;
        display: flex;
        align-self: center;
        color: black;
        justify-self: center;
    }

    .houses {
        display: flex;
        justify-content: center;
    }

  
  </style>
  