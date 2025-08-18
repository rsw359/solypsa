<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<div class="app">
  <Header />
  <main><slot /></main>
  <Footer />
</div>

<style>
  .app {
    min-height: 100svh;        /* full viewport height (safe on mobile) */
    display: flex;
    flex-direction: column;
  }
  main {
    flex: 1;                   /* grows to push footer to the bottom */
    min-width: 0;
  }
</style>
