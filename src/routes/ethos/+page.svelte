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
        <h1>Precision. Depth. Design <em>Solypsa</em></h1>
        <h3>Ethos</h3>
        <p>
          My name is Erik Peel, creator of Solypsa. My goal is to bring analog excellence into focus through carefully curated
          audio equipment and thoughtful design. I believe in the power of sound to transform spaces and experiences. 
        </p>  

        <p>
          Having a lifelong interest in audio, especially vinyl replay (and attendant cultures- DJ, dubplate, audiophile), led me to acquire, setup, and operate a Neumann VMS based mastering studio. This was a formative experience to say the least, teaching me that <em>calibration is critical</em>, and careful attention to the <em>entire</em> chain is more important than any <em>one</em> piece.
        </p>
        <p>
          
          Next came running a brick and mortar HiFi shop along with its owner. I met many great people, and refined of my taste in music replay even further. After that chapter, i took on clients that needed help setting up their prized turntables and full systems. This led to the creation of my analog-centric audio distributorship and consultancy, Solypsa. 
        
        </p>

        <p>Solypsa is the culmination of my passion for music, my technical expertise, and my personal commitment to quality. We offer full service audio distribution, system design, and installation. We also provide comprehensive
          calibration of your existing turntable, tonearm, and cartridge using the best in class tools and years of experience.
        </p>
        <p>
          Operating in the Pacific Northwest, I am proud to represent a select group of lines that embody the trifecta of superb performance, value, and artisanal production. These lines are built with care, often by hand, and always with a dedication to the craft. As a result, there is often some time needed to create upon order.
        </p>

        <p> <a style="font-weight:400; text-decoration:none; color: black;" href="mailto:info@solypsa.com?subject=Custom%20Build%20Inquiry">Get in touch</a> with me to discuss your analog desires, whether digital or analog.</p>
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
    font-size: 1.1rem;
    font-weight: 500;
    margin: 0 0 1rem 0;
    text-align: center;
  }

  .intro-text p {
    margin: 0 0 1rem 0;
    max-width: 65ch;
    margin-inline: auto;
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
