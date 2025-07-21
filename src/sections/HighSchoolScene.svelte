<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">
      {#snippet sticky()}
      {/snippet}
  
      {#snippet scrolly()}
        <h3>They both graduated high school in 2015.</h3>
      {/snippet}
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 180vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/highschool-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 500;
        background-color: #A1BDD9;
        max-width: 550px;
        font-size: 2.4em;
        text-align: center;
        padding: 40px 25px;
        border-radius: 70px;
        display: flex;
        align-self: center;
    }
  
  </style>
  