<!-- src/routes/ethos/+page.svelte -->
<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<div class="page">
  <Header />

  <main class="section">
    <div class="container">
      <div class="intro-text">
        <h1>Design beyond function. <em> Solypsa</em></h1>
        <h3>Ethos</h3>
        <p>
          My name is Erik Peel, creator of Solypsa. My goal is to bring audio excellence into focus through carefully curated equipment and thoughtful design. I believe in the power of music to transform spaces and experiences.
        </p>  

        <p>
          Having a lifelong interest in audio, especially vinyl replay (and attendant cultures- DJ, dubplate, audiophile), led me to acquire, setup, and operate a Neumann VMS based mastering studio. This was a formative experience to say the least, teaching me that calibration is critical, and careful attention to the entire chain is more important than any one piece.
        </p>

        <p>Solypsa is the culmination of my passion for music, my technical expertise, and my personal commitment to quality.
        </p>
        <p>
          I think of myself as a <strong>musical pimp</strong>. Delivering the finest musical hoes to the streets. Whatever your musical pleasure, I can get it for you, baby. In the words of the illustrius Curtis Mayfield, <strong>"Pimping ain't easy, but it's necessary."</strong> 
        </p>

        <p> We offer full service audio sales and distribution, system design, and installation to the HiFi, home and professional markets.</p>
      </div>
    </div>
  </main>

  <Footer />
</div>

<style>
  /* Page skeleton: header / content / footer */
  .page {
    min-height: 100svh;                 /* full viewport height (safe on mobile) */
    display: grid;
    grid-template-rows: auto 1fr auto;  /* Header | main grows | Footer */
  }

  /* Keep your existing look & feel */
  :global(html) { scroll-behavior: smooth; }
  :global(body) {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }

  .section {
    padding: 4rem 1.25rem;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    place-items: center;                 /* center the intro block */
  }

  .intro-text {
    max-width: 700px;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
  }

  .intro-text h1 {
    font-size: 2.4rem;
    font-weight: 600;
    margin: 0 0 1rem 0;
  }

  .intro-text h3 {
    font-size: 1.2rem;
    font-weight: 500;
    margin: 0 0 1rem 0;
    /* text-align: center; */
  }

  .intro-text p {
    margin: 0 0 1rem 0;
    max-width: 70ch;
    margin-inline: auto;
    text-align: justify;
  }

  /* Responsive tweaks */
  @media (max-width: 900px) {
    .section { padding: 3.5rem 1rem; }
    .intro-text h1 { font-size: 2.1rem; }
  }
  @media (max-width: 520px) {
    .section { padding: 3rem 1rem; }
    .intro-text h1 { font-size: 1.9rem; }
  }
</style>
