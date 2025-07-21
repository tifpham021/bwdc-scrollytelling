<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import house from "../images/house.png";
    import apartment from "../images/apartment.png";
    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;

    function inView(node, callback) {
        const observer = new IntersectionObserver(
        ([entry]) => {
            callback(entry.isIntersecting);
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
            <div class="sticky1" use:inView={(val) => (visible1 = val)}
                transition:fade
                class:invisible={!visible1}>
                <h3>
                    Over the next five years, these early disadvantages compound. While many <span>White 
                    homeowners begin building wealth</span> through rising home equity, <span>Black renters face 
                    growing costs</span> without the same opportunities to invest or accumulate assets — widening 
                    the racial wealth gap even further.
                </h3>
            </div>
        <div class="scene2">
            <div class="person-column cierra-column">
                <div class="sticky-content">
                    <div class="cierra">
                        <h2 class="name" use:inView={(val) => (visible2 = val)}
                            transition:fade
                            class:invisible={!visible2}>Cierra</h2>
                        <img src={apartment} alt="red 4 story apartment" class="apartment" use:inView={(val) => (visible3 = val)}
                        transition:fade
                        class:invisible={!visible3}/>
                    </div>
                </div>
                <div class="scroll-text-cierra" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    <h4>
                        <span>Cierra wasn't able to get approved for a mortgage,</span> so 
                        she was left with no choice but to rent.
                    </h4>
                </div>
            </div>
            <div class="person-column laura-column">
                <div class="sticky-content">
                    <div class="laura">
                        <h2 class="name" use:inView={(val) => (visible2 = val)}
                            transition:fade
                            class:invisible={!visible2}>Laura</h2>
                        <img src={house} alt="2 story magenta house" class="house" use:inView={(val) => (visible3 = val)}
                        transition:fade
                        class:invisible={!visible3}/>
                    </div>
                </div>
                <div class="scroll-text-laura" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    <h4>
                    <span>Laura</span> on that other hand <span> quickly approved for a 
                        mortgage</span> and was able to <span> her first home with ease.</span>
                    </h4>
                </div>
            </div>
        </div>
      {/snippet}

    
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Teachers:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 750vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/housing-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #4A6499;
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
        transition: opacity 0.5s ease-in-out;
    }

    .scene2 {
        display: flex;
        margin-top: 50vh;
        height: 450vh;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
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
        transition: opacity 0.5s ease-in-out;
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
        transition: opacity 0.5s ease-in-out;
    }

    .apartment {
        transition: opacity 0.5s ease-in-out;
    }

    h4 {
        font-family: 'Inter', serif;
        font-weight: 300;
        text-align: center;
        background-color: #4c6597;
        font-size: 1.8em;
        max-width: 400px;
        padding: 40px 50px;
        border-radius: 80px;
        color: white;
    }

    .scroll-text-laura, .scroll-text-cierra {
        margin-top: 100vh;
        z-index: 10;
        position: relative;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

  </style>
  