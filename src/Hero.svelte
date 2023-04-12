<script>
  let heroTitle = 'Salmon Cookies';
  let heroSubtitle = 'Looks Like Salmon, Tastes Like Heaven';
  import Details from "./Details.svelte";
</script>

<style>
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 80vh;
    background-color: cadetblue;
  }

  .hero-title {
    font-size: 4rem;
    margin: 0;
  }

  .hero-subtitle {
    font-size: 2rem;
    margin: 0;
  }
</style>

<div class="hero">
  <h1 class="hero-title">{heroTitle}</h1>
  <h2 class="hero-subtitle">{heroSubtitle}</h2>
</div>
<Details />
