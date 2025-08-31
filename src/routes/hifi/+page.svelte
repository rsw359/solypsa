<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import ProductCarousel from '$lib/components/ProductCarousel.svelte';

  const products = [
    {
      id: 'NNNN',
      title: 'NNNN Loudspeakers',
      copy: `<p>What happens when some of the smartest people in audio put together a loudspeaker company?
             You get speakers that break the mold, managing to truly stride across HiFi and Professional requirements,
             smashing expectations along the way. Rune Skramstad, CTO, is pushing the envelope in horn loading and
             performance per size areas.</p> 
             
             <p>Solypsa is proud to be the exclusive distributor for NNNN in North America.</p>`,

      link: {
        url: 'https://nnnn.audio',
        label: 'NNNN →'
      },
             
      images: [
        { src: '/comium-1.jpg', alt: 'Comium 30 front view' },
        { src: '/comium-grill.jpg', alt: 'Comium 30 with grill' },
        { src: '/devor-30.png', alt: 'Devor series' },
        { src: '/Trent-35.png', alt: 'Trent 35/25' },
        { src: '/ON2.png', alt: 'Ojas x NNNN ON2' }
      ]
    },
    {
      id: 'STST',
      title: 'STST Turntables',
      copy: `Stefan Strohmetz, the creator of STST,  never gave up on direct drive. The direct drives of the early 80s offered unparalleled speed, control, and bass reproduction, 
            but often lacked the body and tone colors a truly top class table should offer. Stefan designed a made-in-house low torque motor solution and has been constantly 
            refined his design since 1985! Handmade in Germany, and finished to your specification- such luxury is unheard of in today’s mass produced world. This table is very musical
             and accurate, worlds away from cold and sterile of in many modern productions.<br><br>Stefan offers his own handmade carbon and pom tonearm: the Vertex. A gimbal design in your choice 
             of 9″/10″/12″ lengths. The traditional look hides a labor of love, higlighted by titanium bearing tolerances so fine they took years to perfect. What Stefan has made here is a 
             neutral and musical masterpiece at a serious value! <br><br> We are proud to be the exclusive distributor for STST in North America.`,
      
      link: {
        url: 'https://stst-audio.de',
        label: 'STST →'
      },
      images: [
        { src: '/STST1.jpg', alt: 'stst turntable' },
        { src: '/STST2.jpg', alt: 'stst turntable' },
        { src: '/STST3.jpg', alt: 'stst turntable' },
        { src: '/STST4.jpg', alt: 'stst turntable' },
        { src: '/STST6.jpg', alt: 'stst turntable' },
        { src: '/STST5.jpg', alt: 'stst turntable' },
      ]
    },
    {
      id: 'Audio Creative',
      title: 'Audio Creative Tonearms',
      copy: `Audio Creative, based in the Netherlands, has lovingly created a modern take on the classic high-mass transcription tonearm. Available in 9″, 10″ and 12″ 
      (12″ available with standard connector or SPU A).<br><br>The Groovemaster III features a titanium armwand with silver internal wiring terminating into a 5 pin din output connector. 
      New for V3 is a fine adjustment counterweight making small tweaks to VTF a pleasure.  Options include a sliding SME style mounting base, a simple round base or the heavy weight base 
      with fine and on the fly VTA adjustment. <br><br>Solypsa is a dealer for Audio Creative in North America.
      A small shipping fee from Europe will be added to the order. Contact us to discuss available options and current USD prices.`,
      link: {
        url: 'https://audio-creative.nl',
        label: 'Audio Creative →'
      },
      images: [
        { src: '/AC1.png', alt: 'custom order' },
        { src: '/AC2.jpg', alt: 'custom order' },
        { src: '/AC3.jpg', alt: 'custom order' },
        { src: '/AC4.png', alt: 'custom order' },
      ]
    },
    {
      id: 'Primary Control',
      title: 'Primary Control',
      copy: `Bernd Hemmen makes tonearms and turntables with care and precision in this Amsterdam studio. 
      His tonearms are gimbal (Arrow) or stabilized uni pivots (Reference, Gravity, FCL). 
      His Kinea turntable is a variable torque direct drive.`,

      link: {
        url: 'https://primarycontrol.nl',
        label: 'Primary Control →'
      },
      images: [
        { src: '/PC1.jpg', alt: 'custom order' },
        { src: '/PC2.jpg', alt: 'custom order' },
        { src: '/PC3.png', alt: 'custom order' },
        { src: '/PC4.jpg', alt: 'custom order' },
        { src: '/PC6.png', alt: 'custom order' },
      ]
    },

    {
      id: 'Solypsa Custom',
      title: 'Solypsa Custom',
      copy: `Solypsa Custom is our in-house design and build service. We can create custom solutions for your audio needs, whether it be a bespoke turntable, 
      speaker system, or any other audio equipment. We work closely with you to ensure that your vision is realized with the highest quality craftsmanship.
      At Solypsa we guide you through the entire process, from initial design to final production, ensuring that every detail meets your specifications.
      Our lines are built with care, often by hand, and always with a dedication to the craft.`,

      link: {
        url: 'mailto:info@solypsa.com?subject=Custom%20Build%20Inquiry',
        label: 'Learn more →'
      },


      images: [
        { src: '/dark1.png', alt: 'custom order' },
        
      ]
    },
    
  ];
</script>

<Header />

<!-- NNNN Intro (unchanged) -->
<section id="NNNN" class="section">
  <div class="product-wrapper">
    <div class="intro-text">
      <h1>Solypsa HI-FI</h1>
      <h4>USA distributor for NNNN loudspeakers and STST turntables</h4>
  
      <p>We offer a curated selection of high-end audio products that combine exceptional performance with artisanal craftsmanship.</p>
      <br>
      <!-- <p>
        Interested in becoming a HiFi distribution partner? Please inquire <a style="font-weight:400; color: black;" href="mailto:info@solypsa.com?subject=Custom%20Build%20Inquiry">here</a>.
      </p>
      <br> -->
      <p>
        Solypsa and our partners design with products that meet the highest requirements of both Hi-Fi enthusiasts and professional audio engineers, and our skillful deployment of them as a system ensures the best sound quality possible. We believe in the power of music and the value of excellent audio playback to <em>enhance</em> life and well being. We are committed to providing you with the tools to achieve your vision. Whether you are looking for a turntable, speaker system, or any other audio equipment, we are here to help you find the perfect solution.
      </p>
      <br>
      <p>
        <a style="font-weight:400; text-decoration:none; color: black;" href="mailto:info@solypsa.com?subject=Custom%20Build%20Inquiry">Get in touch</a> with us to learn more about our products and how we can help you achieve your audio goals.
      </p>
      <br>
      <p class="cta">
        Interested in becoming a HI-FI distribution partner? Please inquire
        <a href="mailto:info@solypsa.com?subject=Partner%20Inquiry" style="font-weight:400; color: black; text-decoration: none;">here</a>.
      </p>
      
      <p>For more information on our lines, click <a href="mailto:info@solypsa.com?subject=Lines%20Inquiry" style="font-weight:400; color: black; text-decoration: none;" >here →</a></p>

    </div>
  </div>
</section>

<!-- Carousel for remaining products -->
<section aria-labelledby="products" class="section carousel-section">
  <h2 id="products" class="visually-hidden">Products</h2>
  <ProductCarousel {products} autoplay={true} interval={5500} pauseOnHover={true} />
</section>

<Footer />

<style>
  :global(html) { scroll-behavior: smooth; }
  :global(body) {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }

  .section { padding: 4rem 1.25rem; }

  .product-wrapper {
    max-width: 1200px;
    width: 100%;
    padding: 0 1rem;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  }

  .intro-text {
    max-width: 650px;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 300;
    padding: 0 0 2rem;
  }

  .intro-text h1 {
    font-size: 2.2rem;
    font-weight: 600;
    margin: 0 0 1rem 0;
  }

  .intro-text p {
    margin: 0;
    max-width: 65ch;
    text-align: justify;
    
  }

  .visually-hidden {
    position: absolute !important;
    height: 1px; width: 1px;
    overflow: hidden; clip: rect(1px, 1px, 1px, 1px);
    white-space: nowrap;
  }

  /* Intro text responsive adjustments */
  @media (max-width: 900px) {
    .product-wrapper { justify-content: center; text-align: justify; }
    .intro-text { gap: 1.25rem; text-align: justify; }
    .intro-text h1 { font-size: 1.9rem; }
  }

  @media (max-width: 520px) {
    .product-wrapper { padding: 0; }
    .intro-text { padding: 0 1rem 2rem; text-align: justify; }
    .intro-text h1 { font-size: 1.7rem; }
  }

  /* Carousel section spacing adjustment */
  .carousel-section {
    padding-top: 0.5rem; /* reduced top padding */
  }

  @media (max-width: 520px) {
    .carousel-section {
      padding-top: 0.5rem; /* consistent on small screens */
    }
  }
</style>

