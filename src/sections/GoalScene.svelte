<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import leftHouse from "../images/leftHouse.png";
    import rightHouse from "../images/rightHouse.png";
    import leftSign from "../images/leftSign.png";
    import rightSign from "../images/rightSign.png";
    import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;

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
    <div class="non-flex-wrapper">
        <Scroller layout="right">
        {#snippet sticky()}
        {/snippet}
    
        {#snippet scrolly()}
            <div class="goal-content">
                <h3 use:inView={(val) => (visible1 = val)}
                    transition:fade
                    class:invisible={!visible1}>They both have the goal of owning a house by 30.</h3>
                <div class="houses"
                    use:inView={(val) => (visible2 = val)}
                    transition:fade
                    class:invisible={!visible2}>
                    <div class="left">
                        <img src={leftHouse} alt="two story pink house"/>
                        <img src={leftSign} alt="purple sold sign" class="leftSign"/>
                    </div>
                    <div class="right">
                        <img src={rightSign} alt="blue sold sign" class="rightSign"/>
                        <img src={rightHouse} alt="one story pink house with blue roof"/>
                    </div>
                </div>
            </div>
        {/snippet}
        </Scroller>
    </div>
  </div>
  
  <style>
    @import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
    .background-wrapper {
        position: relative;
        top: 0;
        height: 180vh;
        z-index: 1;
        background-image: url("/bwdc-scrollytelling/goal-scene.png");
        background-position: center;
        background-attachment: fixed;
        justify-content: center;
        align-items: center;
    }

    h3 {
        font-family: 'Inter', serif;
        font-weight: 500;
        background-color: #FCEFAF;
        max-width: 420px;
        font-size: 2.4em;
        text-align: center;
        padding: 30px 35px;
        border-radius: 70px;
        display: flex;
        align-self: center;
        color: black;
        justify-self: center;
        transition: opacity 0.5s ease-in-out;
    }

    .houses {
        display: flex;
        justify-content: center;
        gap: 10%;
        transition: opacity 0.5s ease-in-out;
    }

    .invisible {
      opacity: 0;
    }

    .left, .right {
        display: flex;
    }

    .leftSign {
        margin-left: -90px;
        align-self: flex-end;
        height: 200px;
    }

    .rightSign {
        margin-right: -120px;
        z-index: 1;
        align-self: flex-end;
        height: 180px;
    }


    @media (max-width: 750px) {
      h3 {
        font-size: 2rem;
        max-width: 250px;
      }

      .houses img{
            width: clamp(100px, 2vh, 200px)
        }

    }

    @media (max-width: 900px) {

        .houses img{
            width: clamp(350px, 3vh, 400px)
        }

    }


    @media (max-width: 950px) {
        .houses {
            gap: 0;
        }
    }

    @media (max-width: 1100px) {
        .rightSign, .leftSign {
            display: none;
        }

    }

  
  </style>