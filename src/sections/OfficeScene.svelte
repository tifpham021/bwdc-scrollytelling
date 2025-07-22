<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import cierraIcon from "../images/cierra-smiling.png";
    import lauraIcon from "../images/laura1.png";
    import cierraCheck from "../images/cierraCheck.png";
    import lauraCheck from "../images/lauraCheck.png";
    import { fade } from 'svelte/transition';
    let visible = false;
    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;
    let visible5 = false;
    let visible6 = false;
    let showAmount = false;

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

        {#snippet scrolly()}
        <h3 use:inView={(val) => (visible = val)}
            transition:fade
            class:invisible={!visible}>Debt wasn’t the only difference. 
            When they entered the workforce, 
            inequality followed them through the door.
        </h3>
        <div class="scene2">
            <div class="images"
            use:inView={(val) => (visible1 = val)}
            transition:fade
            class:invisible={!visible1}>
                <img src={cierraIcon} alt="icon of smiling woman with brown hair" class="cierra-icon"/>
                <img src={cierraCheck} alt="check of 60k" class="check"/>
            </div>
                <h4 use:inView={(val) => (visible2 = val)}
                    transition:fade
                    class:invisible={!visible2} class="cierra-salary">Cierra's annual salary was <span class="amount">$60,000.</span></h4>
        </div>
        <div class="scene3">
            <div class="images"
            use:inView={(val) => (visible3 = val)}
            transition:fade
            class:invisible={!visible3}>
                <img src={lauraCheck} alt="check of 72k" class="check"/>
                <img src={lauraIcon} alt="icon of smiling woman with blonde hair" class="laura-icon"/>
            </div>
                <h4 use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4} class="laura-salary">Laura's annual salary was <span class="amount">$72,000.</span>
                </h4>
        </div>
        <div class="scene4" use:inView={(val) => (visible5 = val)}
            transition:fade
            class:invisible={!visible5}>
            <h2>Laura makes <span class="amount">$12,000</span> more than Cierra every year.</h2>
        </div>
        <div class="scene5" use:inView={(val) => (visible6 = val)}
            transition:fade
            class:invisible={!visible6}>
            <h2>That may not seem like much of a difference, but it adds up over time.</h2>
        </div>
      {/snippet}

      {#snippet sticky()}
      {/snippet}

    
    </Scroller>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 580vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/office-scene.png");
        background-position: center;
        background-attachment: fixed;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #1C1C6E;
        color: white;
        max-width: 500px;
        font-size: 2.1em;
        text-align: center;
        padding: 50px;
        border-radius: 120px;
        display: flex;
        align-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    .scene2, .scene3 {
        margin-top: 90vh;
    }

    .scene4 {
        margin-top: 90vh;
        transition: opacity 0.5s ease-in-out;
    }

    .scene4 h2, .scene5 h2 {
        max-width: 500px;
        padding: 40px;
    }

    .scene5 {
        margin-top: 1vh;
        transition: opacity 0.5s ease-in-out;
    }
    
    .images {
        display: flex;
        justify-content: center;
        gap: 40px;
        transition: opacity 0.5s ease-in-out;
    }


    h4, h2 {
        background-color: #1C1C6E;
        color: white;
        text-align: center;
        font-family: 'Inter', serif;
        font-weight: 300;
        font-size: 2em;
        max-width: 700px;
        justify-self: center;
        padding: 30px 40px;
        border-radius: 50px;
        transition: opacity 0.5s ease-in-out;
    }

    .amount {
        font-family: 'Roboto', serif;
        font-weight: 700;
        font-size: 1em;
    }

    .cierra-icon {
        height: 365px;
    }

    .check {
        height: 360px;
    }

    .laura-icon {
        height: 400px;
    }

    .cierra-salary {
        margin-top: 2%;
    }
  </style>
  