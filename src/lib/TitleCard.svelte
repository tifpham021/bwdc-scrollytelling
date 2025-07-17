<script>
  let { title, subtitle } = $props();
</script>

<div class="title-card">
  <div class="content">
    <h1>{title}</h1>
    <p>{subtitle}</p>
  </div>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Mukta+Vaani:wght@800&display=swap');

  .title-card {
    background-image: url("/images/title-page.png");
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 2rem;
    font-family: "Mukta Vaani", sans-serif;
    font-weight: 800;
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

  @media (max-width: 600px) {
    h1 {
      font-size: 3.2rem;
    }

    p {
      font-size: 2rem;
    }
  }
</style>
