<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import house from "../images/house.png";
    import apartment from "../images/apartment.png";
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet sticky()}
      {/snippet}

        {#snippet scrolly()}
            <div class="sticky1">
            
            </div>
        
      {/snippet}

    
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 780vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/laura-house-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #493a6d;
        color: white;
        max-width: 650px;
        font-size: 2em;
        text-align: center;
        padding: 50px;
        border-radius: 90px;
        align-self: center;
    }

    .sticky1 {
        display: flex;
        align-self: center;
    }

    .scene2 {
        display: flex;
        margin-top: 100vh;
        height: 450vh;
    }

    span {
        font-family: 'Teachers', serif;
    }

    .person-column {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 50%;
        margin: 0 auto;
        justify-content: center;
    }


    .name {
        font-family: 'Satisfy', serif;
        text-align: center;
        font-size: 5em;
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

    .house {
        margin-top: 70px;
    }

    h4 {
        font-family: 'Inter', serif;
        text-align: center;
        background-color: #565b85;
        font-weight: 500;
        font-size: 1.6em;
        max-width: 400px;
        padding: 30px 50px;
        border-radius: 80px;
        color: white;
    }

    .scroll-text-laura, .scroll-text-cierra {
        margin-top: 100vh;
        z-index: 10;
        position: relative;
    }

  </style>
  