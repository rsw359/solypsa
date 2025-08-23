<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import partners from '$lib/data/partners.json'; // static import via Vite
</script>

<div class="page">
  <Header />

  <main class="section">
    <div class="container">
      <h2>Partner List</h2>

      <div class="partner-list">
        {#each partners as p, i}
          <a href={p.url} target="_blank" rel="noopener noreferrer">{p.name} →</a>
          {#if i < partners.length - 1}<br>{/if}
        {/each}
      </div>

      <p class="cta">
        Interested in becoming a HiFi distribution partner? Please inquire
        <a href="mailto:info@solypsa.com?subject=Partner%20Inquiry" style="font-weight:400; color: black; text-decoration: none;">here</a>.
      </p>
    </div>
  </main>

  <Footer />
</div>

<style>
  /* Page skeleton (matches other pages) */
  .page {
    min-height: 100svh;
    display: grid;
    grid-template-rows: auto 1fr auto;
  }

  .section { padding: 4rem 1.25rem; }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  /* Typography */
  h1 {
    font-size: 2.2rem;
    font-weight: 600;
    margin: 0 0 2rem 0;
    font-family: 'Helvetica Neue', sans-serif;
  }

  .partner-list {
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
    font-size: 1.1rem;
    margin-bottom: 2rem;
  }

  /* Links: black, no decoration */
  .partner-list a,
  .cta a {
    color: black;
    text-decoration: none;
    transition: opacity 0.2s ease;
  }
  .partner-list a:hover,
  .cta a:hover { opacity: 0.7; }

  .cta {
    margin-top: 2rem;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
  }

  /* Mobile consistency */
  @media (max-width: 600px) {
    h1 { font-size: 1.8rem; }
    .partner-list { font-size: 1rem; }
  }
</style>
