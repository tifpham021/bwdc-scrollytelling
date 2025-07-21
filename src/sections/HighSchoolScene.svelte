<script>
    import Scroller from "../lib/Scroller.svelte";
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
    <Scroller layout="center">
      {#snippet sticky()}
      {/snippet}
  
      {#snippet scrolly()}
        <h3 use:inView transition:fade="{{ duration: 300 }}" class:invisible={!visible}>They both graduated high school in 2015.</h3>
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
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }
  
  </style>
  