<script>
    import Scroller from "../lib/Scroller.svelte";
    import cierra from "../images/cierra-standing2.png";
    import laura from "../images/laura-standing1.png";

    
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet sticky()}
      {/snippet}

        {#snippet scrolly()}
            <div class="scrolly1">
                <img src={cierra} alt="Black woman smiling and waving in a pink shirt and blue shorts" class="cierra"/>
                <h3>
                    The story of Laura and Cierra isn’t just 
                    about two individuals navigating adulthood— 
                    it’s a window into a much larger reality.
                </h3>
                <img src={laura} alt="White woman smiling and waving in a blue dress" class="laura"/>
            </div>
            <div class="scrolly2">
                <h3>
                    
                </h3>
            </div>
      {/snippet}
    </Scroller>
    <div class="scene3">
        <div class="scrolls">
            <div class="scrolly-text1">
                
            </div>
            <div class="scrolly-text2">
                
            </div>
        </div>
            <div class="sticky1">
                
                
            </div>
    </div>
    <div class="scene4">
        
        <h3>
            
        </h3>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 650vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/skyline-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #4A6499;
        color: white;
        max-width: 500px;
        font-size: 2em;
        text-align: center;
        padding: 50px 40px;
        border-radius: 120px;
        align-self: center;
    }

    .scrolly1 {
        display: flex;
        align-self: center;
    }

    .scrolly2 {
        margin-top: 90vh;
        align-self: center;
    }

    .scene3 {
        margin-top: 90vh;
        text-align: center;
        justify-content: space-between;
        height: 240vh;
        display: flex;
        margin: 3%;
    }

    .scrolly-text1 {
        align-self: center;
        background-color: #63528a;
        color: white;
        font-family: 'Inter', serif;
        padding: 40px;
        font-size: 1.6em;
        border-radius: 80px;
        max-width: 550px;
        margin-top: 100vh;
        z-index: 10;
        position: relative;
    }

    .scrolly-text2 {
        align-self: center;
        background-color: #63528a;
        color: white;
        font-family: 'Inter', serif;
        padding: 40px;
        font-size: 1.6em;
        border-radius: 80px;
        max-width: 550px;
        margin-top: 30vh;
        z-index: 10;
        position: relative;
    }

    span {
        font-family: 'Teachers', serif;
    }

    .sticky1 {
        display: flex;
        flex-direction: column;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
    }

    .scene4 {
        display: flex;
        justify-content: center;
    }

    .cierra {
        height: 500px;
    }

    .laura {
        height: 480px;
        width: 250px;
    }

  </style>
  