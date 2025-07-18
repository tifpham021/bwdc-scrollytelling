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
</script>

<div class="park-scene">
  <div class="background-wrapper">
    <Scroller layout="center">
      {#snippet sticky()}{/snippet}

      {#snippet scrolly()}
        <div class="park-content">
          <img src={tree1} alt="tree" class="tree" />
          <div class="center">
            <h1>Here's Who Our Story Will Follow Today</h1>
            <img src={bench} alt="bench" class="bench" />
          </div>
          <img src={tree2} alt="tree" class="tree" />
        </div>

        <div class="character-intro">
          <div class="cierra">
            <img src={cierra1} alt="icon of cierra" class="cierra-img" />
            <h2>This is Cierra</h2>
          </div>
          <div class="laura">
            <img src={laura1} alt="icon of laura" class="laura-img" />
            <h2>This is Laura</h2>
          </div>
        </div>

        <div class="characters-standing">
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
    font-size: 3.7em;
    justify-self: center;
    max-width: 700px;
    margin-top: -15%;
  }

  .bench {
    max-width: 370px;
    display: flex;
    justify-self: center;
  }

  .tree {
    max-width: 500px;
    max-height: 600px;
  }

  .character-intro {
    display: flex;
    justify-content: center;
    gap: 13rem;
    margin-top: 30vh;
  }

  .cierra-img {
    height: 350px;
    width: 350px;
    filter: drop-shadow(0 0 35px #c5ff96c6);
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
    margin-top: 40vh;
    justify-content: center;
  }

  .characters-standing h2 {
    text-align: center;
    color: white;
    font-size: 2.4em;
  }
</style>
