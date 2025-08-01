<script>
  import Header from '$lib/components/Header.svelte';
</script>

<Header />

<!-- Hero Section -->
<section class="hero">
  <div class="intro-wrapper">
    <div class="intro-text">
      <h1>Precision. Depth. Design <em>Solypsa</em></h1>
      <p>
        At Solypsa, we bring analog excellence into focus through carefully curated
        audio equipment and thoughtful design. We believe in the power of sound to
        transform spaces and experiences.
      </p>
      <p>
        Full service audio distribution, system design and installation. Also comprehensive
        calibration of your existing turntable / tonearm / cartridge. Best of class tools and years of experience.
      </p>

      <nav class="nav">
        <a href="#NNNN">NNNN →</a>
        <a href="#ppp">Ethos →</a>
        <a href="/contact">Contact →</a>
      </nav>
    </div>
  </div>
</section>

<!-- NNNN Section -->
<section id="NNNN">
  <div class="product-wrapper">
    <div class="intro-text">
      <h1>NNNN Loudspeakers</h1>
      <p>
        NNNN hail from Oslo. What happens when some of the smartest people in audio put together a loudspeaker company?
        You get speakers that break the mold. They manage to truly stride across HiFi and Professional requirements
        smashing expectations along the way. Rune Skramstad, CTO, happens to be pushing the envelope in horn loading and
        performance per size areas. Oh and in his spare time putting together ultimate systems for ETF…
      </p>
    </div>
  </div>

  <div class="container">
    <!-- Comium 30 -->
    <div class="text">
      <h3>Comium 30</h3>
      <p>
        Designed to mount directly to a wall (or even ceiling) less than 5″ deep. Bringing true mastering monitor
        sound quality to a very design and space conscious form factor. Perfect for modern condo / apartment spaces as
        well as high end boardrooms and gaming environments.
      </p>
    </div>
    <div class="image">
      <div class="image-gallery">
        <img src="/comium-1.jpg" alt="Comium 1" />
        <img src="/comium-2.jpg" alt="Comium 2" />
        <img src="/comium-grill.jpg" alt="Comium Grill" />
      </div>
    </div>

    <!-- Devor -->
    <div class="text">
      <h3>Devor 40/30/23/160</h3>
      <p>
        The horn loaded Devor subwoofer models feature extra low distortion and a sub cardioid dispersion pattern, both
        of which make for easy placement and integration. Ultimate subwoofers for the most demanding systems bar none.
      </p>
    </div>
    <div class="image">
      <div class="image-gallery single">
        <img src="/devor-30.png" alt="Devor" />
      </div>
    </div>

    <!-- Trent -->
    <div class="text">
      <h3>Trent 35/25</h3>
      <p>
        Small footprint, mighty capable. Transmission line loaded subwoofer (12″ or 18″) with omni dispersion pattern.
        Remember that transmission line loaded subs fall off at half the rate below resonant frequency versus a ported
        bass reflex sub, so these dig deep.
      </p>
    </div>
    <div class="image">
      <div class="image-gallery single">
        <img src="/Trent-35.png" alt="Trent" />
      </div>
    </div>

    <!-- Ojas x NNNN -->
    <div class="text">
      <h3>Ojas x NNNN ON series 5</h3>
      <p>
        Four modern reimaginations of the classic large format speaker system, at home in the most demanding audiophile
        systems or clubs. ON7 – ON2 will require large rooms and high power amplification to reach their full potential.
        ON1 is a more compact version that can be used in smaller spaces, but still delivers the same high quality sound.
      </p>
    </div>
    <div class="image">
      <div class="image-gallery single">
        <img src="/ON2.png" alt="ON2" />
      </div>
    </div>
  </div>
</section>

<!-- Ethos Section -->
<section id="ppp">
  <div class="container">
    <div class="text text-section">
      <h2>Lorem ipsum dolor sit amet</h2>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante
        dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris.
      </p>
    </div>
    <div class="image"><!-- Add your image here if needed --></div>
  </div>
</section>


<style>
  :global(html) {
    scroll-behavior: smooth;
  }

  :global(body) {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }

  /* Hero Section */
  .hero {
    padding: 6rem 2rem 4rem;
    display: flex;
    justify-content: center;
    background-color: #eef1f2;
  }

  .intro-wrapper {
    max-width: 1200px;
    width: 100%;
    display: flex;
    justify-content: flex-end;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  }

  .intro-text {
    max-width: 600px;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
  }

  .nav {
    display: flex;
    gap: 1rem;
    margin: 1rem 0 3rem;
    justify-content: center;
  }

  .nav a {
    text-decoration: none;
    color: black;
  }

  /* Product Section */
  .product-wrapper {
    max-width: 1200px;
    width: 100%;
    padding: 0 2rem;
    display: flex;
    justify-content: flex-end;
  }

  section {
    padding: 4rem 2rem;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .text {
    flex: 1 1 400px;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
  }

  .text-section {
    border-top: 1px solid rgba(0, 0, 0, 0.1);
    padding-top: 2rem;
  }

  .image-gallery {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1rem;
    margin-top: 2rem;
    padding-bottom: 100px;
  }

  .image-gallery img {
    max-width: 200px;
    width: 100%;
    height: auto;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.3s ease;
  }

  .image-gallery img:hover {
    transform: scale(1.05);
  }

  .image-gallery.single {
    justify-content: center;
    padding-bottom: 100px;
  }

  .image-gallery.single img {
    max-width: 400px;
    cursor: default;
  }

  /* Headings */
  h1 {
    font-size: 2.5rem;
    font-weight: 600;
    margin-bottom: 1rem;
  }

  h2 {
    font-size: 2rem;
    font-weight: 600;
    margin-bottom: 0.75rem;
  }

  h3 {
    font-size: 1.5rem;
    font-weight: 500;
    margin-top: 2rem;
  }

  p {
    font-size: 1rem;
    margin-bottom: 1rem;
    max-width: 600px;
  }

  /* Responsive Styles */
  @media (max-width: 768px) {
    .hero,
    .intro-wrapper,
    .product-wrapper,
    .container {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .intro-text,
    .text {
      text-align: center;
    }

    .image-gallery,
    .image-gallery.single {
      justify-content: center;
    }

    .image-gallery img,
    .image-gallery.single img {
      max-width: 90%;
    }

    h1 {
      font-size: 2rem;
    }

    h2 {
      font-size: 1.5rem;
    }
  }
</style>


