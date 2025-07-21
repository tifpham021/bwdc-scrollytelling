<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import debt from "../images/debt.png";
    import debtFree from "../images/debt-free.png";

    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;

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
        <div class="person-column">
            <div class="sticky-content" use:inView={(val) => (visible1 = val)}
                transition:fade
                class:invisible={!visible1}>
                <div class="cierra">
                    <h2>Cierra</h2>
                    <img src={debt} alt="shows that person is running out of time to pay their debts with an hourglass and a chart"/>
                </div>
            </div>
            <div class="scroll-text-cierra" 
                use:inView={(val) => (visible3 = val)}
                transition:fade
                class:invisible={!visible3}>
                <p>Cierra graduated with <span>over $30,000 in student loans and no financial help from family.</span></p>
                <p>She had to begin repaying her loans immediately after graduation.</p>
                <p>This financial pressure shaped her job choices.</p>
            </div>
        </div>
      <Scroller layout="center">
        {#snippet sticky()}
        {/snippet}
  
        {#snippet scrolly()}
        <div class="scrolly-content-1" 
            use:inView={(val) => (visible2 = val)}
            transition:fade
            class:invisible={!visible2}>
            <h3>
                From now on, their journeys will look entirely different— shaped not by effort 
                or ambition, but by systems they never controlled.
            </h3>
        </div>
        {/snippet}
      </Scroller>
        <div class="person-column">
            <div class="sticky-content" use:inView={(val) => (visible1 = val)}
                transition:fade
                class:invisible={!visible1}>
                <div class="laura">
                    <h2>Laura</h2>
                    <img src={debtFree} alt="shows that person debt free"/>
                </div>
            </div>
            <div class="scroll-text-laura"
                use:inView={(val) => (visible3 = val)}
                transition:fade
                class:invisible={!visible3}>
                <p>Laura graduated <span>debt-free with help from her family.</span></p>
                <p>She had more freedom to explore job opportunities.</p>
                <p>She could afford to take lower-paying internships.</p>
            </div>
        </div>
    </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter&display=swap");
    .background-wrapper {
      position: relative;
      top: 0;
      z-index: 1;
      background-image: url("/bwdc-scrollytelling/split-screen-scene.png");
      background-position: center;
      background-attachment: fixed;
      height: 350vh;
      display: flex;
      justify-content: center;
      grid-template-columns: 1fr 1fr 1fr;
    }

    .sticky-content {
        display: flex;
        height: 100vh;
        position: sticky;
        top: 0;
        align-items: center;
        justify-content: center;
        z-index: 2;
        transition: opacity 0.5s ease-in-out;
    }

    .sticky-content h2 {
        color: white;
        text-align: center;
        font-family: 'Satisfy', serif;
        font-size: 5.5em;
    }

    .scrolly-content-1 {
        margin-top: 30vh;
        color: white;
        text-align: center;
        background-color: #734059;
        font-size: 1.7em;
        border-radius: 80px;
        max-width: 450px;
        padding: 20px 40px;
        position: relative;
        font-family: 'Inter', serif;
        font-weight: 500;
        transition: opacity 0.5s ease-in-out;
    }

    .scrolly-content-1 h3 {
        font-family: 'Inter', serif;
        font-weight: 500;
    }

    .cierra {
        margin-top: -35%;
        justify-content: center;
        align-content: center;
        margin-right: -35%;
    }

    .scroll-text-cierra {
        transform: translateX(20%);
        transition: opacity 0.5s ease-in-out;
    }

    .cierra img, .laura img {
        margin-top: -30px;
    }

    .laura {
        margin-top: -35%;
        margin-left: -35%;
    }

    .scroll-text-laura {
        transform: translateX(-18%);
        transition: opacity 0.5s ease-in-out;
    }

    .laura img {
        width: 380px;
    }

    .scroll-text-cierra, .scroll-text-laura{
        margin-top: 140vh;
        text-align: center;
        background-color: #DD9EBC;
        border-radius: 50px;
        position: relative;
        z-index: 10;
        padding: 20px;
    }

    .scroll-text-cierra p, .scroll-text-laura p {
        color: black;
        font-family: 'Inter', serif;
        font-weight: 300;
        font-size: 1.5em;
        max-width: 400px;
        justify-self: center;
    }

    .person-column {
        display: flex;
        flex-direction: column;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
    }

    .invisible {
      opacity: 0;
    }

  </style>
  