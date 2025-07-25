<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import tree1 from "../images/tree1.png";
  import tree2 from "../images/tree2.png";
  import bench from "../images/bench.png";
  import cierra1 from "../images/cierra1.png";
  import laura1 from "../images/laura1.png";
  import cierraStanding from "../images/cierra-standing1.png";
  import lauraStanding from "../images/laura-standing1.png";
  import { fade } from "svelte/transition";

  let visible1 = false;
  let visibleText = false;
  let visibleBench = false;
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
      },
    };
  }
</script>

<div class="park-scene">
  <div class="background-wrapper">
    <Scroller layout="center">
      {#snippet sticky()}{/snippet}

      {#snippet scrolly()}
        <div class="park-content">
          <img
            src={tree1}
            alt="tree"
            class="tree"
            use:inView={(val) => (visible1 = val)}
            transition:fade
            class:invisible={!visible1}
          />
          <div class="center">
            <h1
              use:inView={(val) => (visibleText = val)}
              transition:fade
              class:invisible={!visibleText}
              class="park-text"
            >
              Here's Who Our Story Will Follow Today
            </h1>
            <img
              src={bench}
              alt="bench"
              class="bench"
              use:inView={(val) => (visibleBench = val)}
              transition:fade
              class:invisible={!visibleBench}
            />
          </div>
          <img
            src={tree2}
            alt="tree"
            class="tree"
            use:inView={(val) => (visible1 = val)}
            transition:fade
            class:invisible={!visible1}
          />
        </div>

        <div
          class="character-intro"
          use:inView={(val) => (visible2 = val)}
          transition:fade
          class:invisible={!visible2}
        >
          <div class="cierra">
            <img src={cierra1} alt="icon of cierra" class="cierra-img" />
            <h2>This is Cierra</h2>
          </div>
          <div class="laura">
            <img src={laura1} alt="icon of laura" class="laura-img" />
            <h2>This is Laura</h2>
          </div>
        </div>

        <div
          class="characters-standing"
          use:inView={(val) => (visible3 = val)}
          transition:fade
          class:invisible={!visible3}
        >
          <div class="cierra-standing">
            <img
              src={cierraStanding}
              alt="cierra standing"
              class="cierra-standing-img"
            />
            <h2>Cierra</h2>
          </div>
          <div class="laura-standing">
            <img
              src={lauraStanding}
              alt="laura standing"
              class="laura-standing-img"
            />
            <h2>Laura</h2>
          </div>
        </div>
      {/snippet}
    </Scroller>
  </div>
</div>

<style>
  @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@700&display=swap");
  @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap");
  .background-wrapper {
    position: relative;
    top: 0;
    z-index: 1;
    background-image: url("/bwdc-scrollytelling/park-scene.png");
    background-position: center;
    background-attachment: fixed;
  }

  .park-content {
    display: flex;
    justify-content: center;
  }

  .park-content h1 {
    border: none;
    color: white;
    background-color: transparent;
    text-align: center;
    font-family: "IBM Plex Mono", serif;
    font-size: 3.7rem;
    justify-self: center;
    max-width: 700px;
    margin-top: -15%;
  }

  .bench {
    max-width: 370px;
    display: flex;
    justify-self: center;
    transition: opacity 0.5s ease-in-out;
  }

  .tree {
    max-width: 500px;
    max-height: 600px;
    transition: opacity 0.5s ease-in-out;
  }

  .park-text {
    transition: opacity 0.5s ease-in-out;
  }

  .character-intro {
    display: flex;
    justify-content: center;
    gap: 13rem;
    margin-top: 90vh;
    transition: opacity 0.5s ease-in-out;
  }

  .cierra-img {
    height: 350px;
    width: 350px;
    filter: drop-shadow(0 0 35px #c5ff96c6);
    margin-bottom: 9%;
  }

  .laura-img {
    height: 400px;
    width: 350px;
    filter: drop-shadow(0 0 35px #c5ff96c6);
  }

  .character-intro h2 {
    color: white;
    font-family: "Roboto", sans-serif;
    background-color: #d19397;
    text-align: center;
    font-size: 2.4em;
    padding: 15px;
    border-radius: 50px;
    max-width: 290px;
  }

  .laura h2 {
    margin-top: -5%;
  }

  .characters-standing {
    display: flex;
    margin-top: 90vh;
    justify-content: center;
    transition: opacity 0.5s ease-in-out;
  }

  .characters-standing h2 {
    text-align: center;
    color: white;
    font-size: 2.4em;
  }

  .invisible {
    opacity: 0;
  }

  @media (max-width: 991px) {
    .park-content h1 {
      max-width: 300px;
      margin-top: 5%;
      font-size: 1.5rem;
    }

    .background-wrapper {
      background-attachment: block;
    }
  }

  @media (max-width: 1009px) {
    .park-content {
      justify-content: center;
      margin: 0 auto;
    }

    .park-content h1 {
      font-size: 2rem;
      max-width: 500px;
    }

    .character-intro {
      flex-direction: column;
      margin: 0 auto;
    }
  }

  @media (max-width: 1125px) {
    .tree {
      display: none;
    }
  }

  @media (max-width: 1201px) {
    .park-content h1 {
      font-size: 3rem;
    }
  }
</style>
