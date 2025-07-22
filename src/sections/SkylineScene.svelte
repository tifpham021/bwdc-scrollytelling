<script>
    import Scroller from "../lib/Scroller.svelte";
    import cierra from "../images/cierra-standing2.png";
    import laura from "../images/laura-standing1.png";
    import map from "../images/US-map.png";
    import freeFromDebt from "../images/free-from-debt.png";
    import homebuyer from "../images/getting-home.png";
    import goodCredit from "../images/good-credit.png";
    
    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;
    let visible4 = false;
    let visible5 = false;
    let visible6 = false;
    let visible7 = false;
    let visible8 = false;
    let visible9 = false;
    let visible10 = false;
    let visible11 = false;
    let visible12 = false;
    let visible13 = false;
    let visible14 = false;

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

    let featuresScene3 = [
        'Improves credit scores',
        'Lowers debt-to-income ratios',
        'Helps millions with homeownership'
    ];

    
    let visibleCount = 1;

    function showMore() {
        if (visibleCount < featuresScene3.length) {
        visibleCount += 1;
        }
    }

    let featuresScene4 = [
        'Gives down payment support to individuals without family wealth',
        'Allow more people to build',
        'Allow more people to build their home equity'
    ];

    let visibleCount1 = 1;

    function showMore1() {
        if (visibleCount1 < featuresScene4.length) {
        visibleCount1 += 1;
        }
    }

    let featuresScene5 = [
    "Updates credit models to include more expenses",
    "Incorporates alternative data like rent and utility payments",
    "Improves access to credit for underserved communities"
  ];

  let visibleCount2 = 1;

    function showMore2() {
        if (visibleCount2 < featuresScene5.length) {
        visibleCount2 += 1;
        }
    }
  </script>
  
  <div class="background-wrapper">
    <Scroller layout="center">

        {#snippet sticky()}
      {/snippet}

        {#snippet scrolly()}
            <div class="scrolly1" use:inView={(val) => (visible1 = val)}
                transition:fade
                class:invisible={!visible1}>
                <img src={cierra} alt="Black woman smiling and waving in a pink shirt and blue shorts" class="cierra"/>
                <h3>
                    The story of Laura and Cierra isn’t just 
                    about two individuals navigating adulthood— 
                    it’s a window into a much larger reality.
                </h3>
                <img src={laura} alt="White woman smiling and waving in a blue dress" class="laura"/>
            </div>
            <div class="scrolly2">
                <img src={map} alt="blank blue map of the United States" class="map" use:inView={(val) => (visible2 = val)}
                transition:fade
                class:invisible={!visible2}/>
                <h3 class="map-text" use:inView={(val) => (visible3 = val)}
                    transition:fade
                    class:invisible={!visible3}>
                    It <span>reflects the systemic forces</span> that shape who 
                    gets to build wealth in America, and who is left 
                    behind <span>even when they work just as hard.</span>
                </h3>
            </div>
            <div class="scrolly2">
                <h3 class="after-map-text" use:inView={(val) => (visible4 = val)}
                    transition:fade
                    class:invisible={!visible4}>
                    But this story doesn’t have to end in inequality. 
                    Let’s look at some current solutions and how we can begin 
                    to close the racial wealth gap.
                </h3>
            </div>
      {/snippet}
    </Scroller>
    <div class="scene3">
            <div class="sticky1" use:inView={(val) => (visible5 = val)}
                transition:fade
                class:invisible={!visible5}>
                <h1 class="scene-header">1. Student Loan Forgiveness</h1>
                <img src={freeFromDebt} alt="guy cutting off the burden of chain of debt" class="debt-free"/>
            </div>
            <div class="scrolls">
                <div class="scrolly-text1" use:inView={(val) => (visible6 = val)}
                    transition:fade
                    class:invisible={!visible6}>
                    <h2>What it Does</h2>
                    <ul>
                        {#each featuresScene3.slice(0, visibleCount) as feature}
                          <li>{feature}</li>
                        {/each}
                      </ul>
                      {#if visibleCount < featuresScene3.length}
                        <button on:click={showMore}>Show More</button>
                      {/if}
                        
                </div>
                <div class="scrolly-text2" use:inView={(val) => (visible7 = val)}
                    transition:fade
                    class:invisible={!visible7}>
                    <h2>Importance</h2>
                    <p>
                        <span>Student loans were the starting point</span> that 
                        widened the financial gap between Cierra and 
                        Laura. Providing debt relief would ease that 
                        burden on those who had to self-fund their education.
                    </p>
                </div>
            </div>
    </div>
    <div class="scene4">
        <div class="scrolls">
            <div class="scrolly-text1" use:inView={(val) => (visible8 = val)}
                transition:fade
                class:invisible={!visible8}>
                <h2>What it Does</h2>
                <ul>
                    {#each featuresScene4.slice(0, visibleCount1) as feature}
                      <li>{feature}</li>
                    {/each}
                  </ul>
                  {#if visibleCount1 < featuresScene4.length}
                    <button on:click={showMore1}>Show More</button>
                  {/if}
            </div>
            <div class="scrolly-text2" use:inView={(val) => (visible9 = val)}
                transition:fade
                class:invisible={!visible9}>
                <h2>Importance</h2>
                <p>
                    <span>Family support gave Laura a head start into homeownership,</span> 
                    while Cierra, without that help, remained a renter. <span>Expanding 
                    down payment assistance programs</span> can help close this gap and expand access 
                    to homeownership.
                </p>
            </div>
        </div>
        <div class="sticky1" use:inView={(val) => (visible10 = val)}
            transition:fade
            class:invisible={!visible10}>
            <h1 class="scene-header">2. First-Generation Homebuyer<br> Assistance</h1>
            <img src={homebuyer} alt="guy cutting off the burden of chain of debt" class="debt-free"/>
        </div>
    </div>
    <div class="scene5">
        <div class="sticky1" use:inView={(val) => (visible11 = val)}
            transition:fade
            class:invisible={!visible11}>
            <h1 class="scene-header">3. Inclusive Credit<br> Scoring Reform</h1>
            <img src={goodCredit} alt="guy cutting off the burden of chain of debt" class="debt-free"/>
        </div>
        <div class="scrolls">
            <div class="scrolly-text1" use:inView={(val) => (visible12 = val)}
                transition:fade
                class:invisible={!visible12}>
                <h2>What it Does</h2>
                <ul>
                    {#each featuresScene5.slice(0, visibleCount2) as feature}
                      <li>{feature}</li>
                    {/each}
                  </ul>
                  {#if visibleCount2 < featuresScene5.length}
                    <button on:click={showMore2}>Show More</button>
                  {/if}
            </div>
            <div class="scrolly-text2" use:inView={(val) => (visible13 = val)}
                transition:fade
                class:invisible={!visible13}>
                <h2>Importance</h2>
                <p>
                    Cierra’s credit score was largely impacted by her <span>debt-to-income 
                    ratio, which put her at a disadvantage</span> when applying for mortgages. 
                    <span>Improving credit access</span> and <span>rethinking score calculations</span> could <span>level 
                    the playing field for millions.</span>
                </p>
            </div>
        </div>
    </div>
    <div class="scene6" use:inView={(val) => (visible14 = val)}
        transition:fade
        class:invisible={!visible14}>
        <h3>
            The racial wealth gap wasn’t created overnight and it won’t be solved overnight either. 
            But by recognizing how factors like student debt, unequal family wealth, and credit barriers 
            can significantly shape opportunity, <span>we can begin to build a more equitable future. </span><br><br>
            Wealth shouldn’t depend on what you’re born with. <span>Wealth should be something everyone has the equal 
            chance to build.</span>
        </h3>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Tenor+Sans&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Satisfy&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 1680vh;
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
        transition: opacity 0.5s ease-in-out;
    }

    .scrolly2 {
        margin-top: 90vh;
        display: flex;
        flex-direction: column;
        align-content: center;
    }

    .scene3, .scene4, .scene5 {
        margin-top: 90vh;
        text-align: center;
        justify-content: center;
        height: 280vh;
        display: flex;
        margin: 3%;
        margin-top: 50vh;
    }

    .scene-header {
        font-size: 2.5em;
    }
    
    .scrolls {
        margin: 0 auto;
    }

    .scrolly-text1 {
        align-self: center;
        background-color: rgba(255, 255, 255, 0.973);
        color: black;
        font-family: 'Inter', serif;
        font-weight: 300;
        padding: 30px 40px 50px 40px;
        font-size: 1.6em;
        border-radius: 100px;
        max-width: 450px;
        margin-top: 100vh;
        z-index: 10;
        position: relative;
        transition: opacity 0.5s ease-in-out;
    }

    .scrolly-text2 {
        align-self: center;
        background-color: rgba(255, 255, 255, 0.973);
        color: black;
        font-family: 'Inter', serif;
        font-weight: 300;
        padding: 40px 70px;
        font-size: 1.6em;
        border-radius: 100px;
        max-width: 380px;
        margin-top: 70vh;
        z-index: 10;
        position: relative;
        transition: opacity 0.5s ease-in-out;
    }

    span {
        font-family: 'Roboto', serif;
        font-weight: 500;
        font-size: 1em;
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
        margin: 0 auto;
        transition: opacity 0.5s ease-in-out;
    }

    .scene4 {
        display: flex;
        justify-content: center;
        height: 290vh;
    }

    .scene5 {
        height: 290vh;
    }

    .cierra {
        height: 500px;
    }

    .laura {
        height: 480px;
        width: 250px;
    }

    .map {
        height: 500px;
        width: 900px;
        align-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .map-text {
        font-family: 'Inter', serif;
        font-weight: 300;
        background-color: #4A6499;
        color: white;
        max-width: 760px;
        font-size: 1.6em;
        text-align: center;
        padding: 30px;
        border-radius: 60px;
        align-self: center;
        margin: 5%;
        transition: opacity 0.5s ease-in-out;
    }

    .after-map-text {
        font-size: 2em;
        padding: 70px 50px;
        max-width: 500px;
        transition: opacity 0.5s ease-in-out;
    }

    h2 {
        font-family: 'Inter', serif;
        margin: 15px;
    }

    .debt-free {
        background-color: #cfe4fcf6;
        padding: 40px 20px;
        border-radius: 40px;
    }

    .scene6 {
        display: flex;
        justify-content: center;
        margin-top: 85vh;
    }

    .scene6 h3 {
        max-width: 700px;
        padding: 70px;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    button {
        border: none;
        font-weight: 700;
        padding: 20px;
        border-radius: 40px;
        font-family: 'Roboto', serif;
        font-size: 1.2rem;
        background-color: #77a2d3f6;
        box-shadow: 1px 2px 2px #415872f6;
    }

    button:hover {
        box-shadow: 1px 3px 3px #2d3d4ff6;
        transform: translateY(3px);
    }

    button:active {
        box-shadow: 1px 3px 3px #415872f6;
        transform: scale(0.98);
    }

  </style>
  