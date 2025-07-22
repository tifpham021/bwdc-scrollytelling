<script>
    import titleBackground from "../images/title-page.png";
    console.log("parkScene URL:", titleBackground);
    import { fly } from 'svelte/transition'
    import { backOut } from 'svelte/easing'
    import { onMount, tick } from 'svelte';
  
    let visible = false;
    let observerEl;
  
    onMount(() => {
      const observer = new IntersectionObserver(
        ([entry]) => {
          if (entry.isIntersecting) {
            visible = true;
            entry.isIntersecting; // Only animate once
          }
        },
        {
          threshold: 0.4, // Trigger when ~40% is visible
        }
      );
      if (observerEl) observer.observe(observerEl);
    });
  
    onMount(async () => {
      await tick();
      visible = true;
    });
  
  </script>
  
  <div class="title-card" style={`background-image: url('${titleBackground}')`} bind:this={observerEl}>
    {#if visible}
      <div class="content">
        <div class="top">
        <h1 in:fly={{ y: 100, duration: 800, easing: backOut }}>Same Degree, </h1>
        <h1 in:fly={{ y: 100, delay: 400, duration: 800, easing: backOut }}>Different Doors</h1>
        </div>
        <p in:fly={{ y: 100, delay: 800, duration: 800, easing: backOut }}>By: Tiffany Pham</p>
      </div>
    {/if}
  </div>
  
  <style>
  @import url('https://fonts.googleapis.com/css2?family=Mukta+Vaani:wght@800&display=swap');
  
    .title-card {
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 2rem;
      font-family: "Mukta Vaani", sans-serif;
      font-weight: 800;
      z-index: 10;
      background-size: cover;
      background-position: center;
      position: relative;
    }
  
    .top {
      display: flex;
      gap: 15px;
    }
  
    .content {
      max-width: 1200px;
      padding: 2rem;
      border-radius: 2rem;
    }
  
    h1 {
      font-size: 5rem;
      margin: 0;
      color: white;
    }
  
    p {
      font-size: 3.5rem;
      color: white;
      margin-top: 1rem;
    }
  
    .lines {
      max-width: 800px;
      font-size: 3rem;
      font-weight: 900;
      text-align: center;
  
      .overflow {
        display: inline-block;
        overflow: hidden;
        vertical-align: bottom;
      }
  
      .line {
        display: inline-block;
        margin: 0.2rem;
        text-transform: uppercase;
        text-shadow: 2px 0 10px hsl(0 0% 0% / 20%);
      }
    }
  
    @media (max-width: 600px) {
      h1 {
        font-size: 3.2rem;
      }
  
      p {
        font-size: 2rem;
      }

    }

    @media (max-width: 1309px) {
        .top {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
    }

  </style>
  

