<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

</script>

<div class="background-wrapper">
    <div class="park-scene"></div>
</div>
  <Scroller layout="left">
    {#snippet sticky()}
    {/snippet}

    {#snippet scrolly()}
    <p class="fade-text">This text will fade in as you scroll</p>
    <p class="fade-text">More scroll-animated text here</p>
    {/snippet}
  </Scroller>

<style>

.background-wrapper {
  position: sticky;
  top: 0;
  height: 100vh;
  z-index: -1; /* behind content */
  overflow: hidden;
}
  .park-scene {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: url("/images/park-scene.png");
    background-size: cover;
    background-position: center;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
</style>
