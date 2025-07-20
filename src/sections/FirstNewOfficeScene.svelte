<script>
    import Scroller from "../lib/Scroller.svelte";

  </script>
  
  <div class="background-wrapper">
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="curtains-content">
                <h3>
                    By the time Cierra and Laura neared 30 
                    and were applying for mortgages to buy their 
                    first homes, the consequences of earlier financial 
                    decisions had already begun to limit one of their options.
                </h3>
            </div>
        {/snippet}
        </Scroller>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@100&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 180vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/office2-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Tenor Sans', serif;
        font-weight: 400;
        background-color: #35647b;
        max-width: 620px;
        font-size: 2.2em;
        text-align: center;
        padding: 50px 65px;
        border-radius: 120px;
        display: flex;
        align-self: center;
        color: white;
        justify-self: center;
    }
  </style>
  