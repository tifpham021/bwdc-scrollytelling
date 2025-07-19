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
                <h3>At this point, Cierra and Laura's paths may look identical from the outside— but financially, 
                    their realities are already worlds apart.
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
        background-image: url("/bwdc-scrollytelling/curtains-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Tenor Sans', serif;
        font-weight: 400;
        background-color: #652946;
        max-width: 620px;
        font-size: 2.2em;
        text-align: center;
        padding: 50px 45px;
        border-radius: 120px;
        display: flex;
        align-self: center;
        color: white;
        justify-self: center;
    }
  </style>
  