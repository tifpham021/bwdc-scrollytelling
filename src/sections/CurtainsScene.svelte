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
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="curtains-content">
                <h3 use:inView transition:fade="{{ duration: 300 }}" class:invisible={!visible}>At this point, Cierra and Laura's paths may look identical from the outside— but financially, 
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
        font-family: 'Inter', serif;
        font-weight: 300;
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
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    @media (max-width: 1009px) {

      .background-wrapper {
        
      }
      h3 {
        font-size: clamp(1.6rem, 4vw, 2.2rem);
        transform: translateY(100%);
      }

    }
  </style>
  