<script>
  import Header from '$lib/components/Header.svelte';
</script>

<Header />

<!-- Hero Section -->


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

       <!-- <nav class="nav">
        <a href="#comium">Comium →</a>
        <a href="#devor">Devor →</a>
        <a href="#trent">Trent →</a>
        <a href="#ojas">OJAS x NNNN →</a>
      </nav> -->
    </div>
  </div>

  <div class="container">
    <!-- Comium 30 -->
    <div class="text" id="comium">
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
    <div class="text" id="devor">
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
    <div class="text" id="trent">
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
    <div class="text" id="ojas">
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

  .intro-text {
    max-width: 600px;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
    margin-bottom: 5rem;
  }

  /* .nav {
    display: flex;
    gap: 1rem;
    margin: 1rem 0 3rem;
    justify-content: center;
    
  }

  .nav a {
    text-decoration: none;
    color: black;
  } */

  /* Product Section */
  .product-wrapper {
    max-width: 1200px;
    width: 100%;
    padding: 0 2rem;
    display: flex;
    justify-content: flex-end;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
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

  /* .text-section {
    border-top: 1px solid rgba(0, 0, 0, 0.1);
    padding-top: 2rem;
  } */

  .image-gallery {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1rem;
    margin-top: 10rem;
    /* padding-bottom: 50px; */
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

    
  }
</style>


