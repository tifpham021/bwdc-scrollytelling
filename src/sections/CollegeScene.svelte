<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">
      {#snippet sticky()}
      {/snippet}
  
      {#snippet scrolly()}
        <h3>They both majored in Finance at the University of Georgia.</h3>
      {/snippet}
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 180vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/college-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Tenor Sans', serif;
        background-color: #A1BDD9;
        max-width: 550px;
        font-size: 2.7em;
        text-align: center;
        padding: 40px 25px;
        border-radius: 40px;
        display: flex;
        align-self: center;
    }
  
  </style>
  