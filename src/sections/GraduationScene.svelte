<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import cierraGrad from "../images/cierra-grad.png";
    import lauraGrad from "../images/laura-grad.png";
    import { fade } from 'svelte/transition';

    let visible = false;

    function inView(node) {
    const observer = new IntersectionObserver(
      ([entry]) => {
        visible = entry.isIntersecting;
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
        <Scroller layout="right" class="no-padding">
        {#snippet sticky()}
            <div class="grad-stage">
                <h1>Class of 2019</h1>
                <div class="grad-icons">
                    <img src={cierraGrad} alt="girl with grad cap" class="grad-cierra"/>
                    <img src={lauraGrad} alt="girl with grad cap" class="grad-laura"/>
                </div>
            </div>
        {/snippet}
    
        {#snippet scrolly()}
        <div class="scrolly">
            <h3 use:inView transition:fade="{{ duration: 300 }}" class:invisible={!visible}>Both women graduated college in 2019 with their Bachelor's in Finance.</h3>
        </div>
        {/snippet}
        </Scroller>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=The+Nautigal:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    .background-wrapper {
        height: 250vh;
        display: flex;
        background-color: #A1BDD9;
    }

    .non-flex-wrapper {
        width: 100%;
        display: block;
    }

    .grad-stage {
        height: 100vh;
        background-image: url("/bwdc-scrollytelling/stage.png");
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
        z-index: 1;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 900px;
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
        font-family: 'Inter', serif;
        font-weight: 500;
        background-color: #4175A9;
        max-width: 300px;
        font-size: 2.2em;
        text-align: center;
        padding: 40px 25px;
        border-radius: 70px;
        display: flex;
        align-self: center;
        color: white;
        justify-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    .grad-icons {
        display: flex;
        gap: 50px;
        margin-top: -5%;
    } 

    .grad-cierra {
        width: 300px;
        height: 300px;
    }

    .grad-laura {
        width: 290px;
        height: 330px
    }

    .scrolly {
        height: 250vh;
        align-content: center;
    }
  
  </style>
  