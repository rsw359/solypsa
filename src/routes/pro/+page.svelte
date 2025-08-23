<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  // Simple gallery data (swap these with your real paths)
  const proGallery = [
    { src: '/Pro1.png', alt: 'Venue system install' },
    { src: '/Pro2.png', alt: 'FOH / reference chain' },
    { src: '/Pro3.png', alt: 'Custom integration' }
  ];

  // Lightbox state
  let lbOpen = false;
  let lbIndex = 0;

  function openLB(i) {
    lbIndex = i ?? 0;
    lbOpen = true;
  }
  const closeLB = () => (lbOpen = false);

  // Keyboard: Esc closes
  function onWinKey(e) {
    if (!lbOpen) return;
    if (e.key === 'Escape') {
      e.preventDefault();
      closeLB();
    }
  }

  function onBackdropKey(e) {
  if (e.key === 'Escape' || e.key === 'Enter' || e.key === ' ') {
    e.preventDefault();
    closeLB();
  }
}

</script>

<svelte:window on:keydown={onWinKey} />

<div class="page">
  <Header />

  <main class="section">
    <div class="container">
      <div class="intro-text">
        <h1>Precision. Depth. Design. <em> Solypsa</em></h1>
        <h3>Solypsa Pro</h3>

        <p>
          For performance spaces, studios, and touring engineers, Solypsa Pro and our partners deliver
          beautiful sound with uncompromising reliability. From horn-loaded systems with studio-grade accuracy, to compact solutions that tame difficult rooms, we build rigs that translate intent—night after night.
        </p>

        <p>
         We only represent select manufacturers whose products excel under pressure, and we never forget music's power for emotional connection.
         We <strong>specify, source, and integrate gear beyond our own lines</strong>, even one off customs, when it serves
          the brief. Whether you need turnkey venue sound, a reference playback chain, or someting unique to your needs, we
          tailor a system to your room, budget, and timeline.
        </p>

        <p>
          Services include needs assessment, system design, acoustic guidance, deployment, and
          calibration. We support venue staff and engineers with documentation and
          follow-up, so your system keeps performing long after opening night.
        </p>

        <p class="cta">
          <a href="mailto:info@solypsa.com?subject=Solypsa%20Pro%20Consultation">
            Start a Solypsa Pro consultation →
          </a>
        </p>
      </div>
    </div>

    <!-- NEW: 3-image gallery -->
    <section class="pro-gallery" aria-label="Solypsa Pro gallery">
      {#each proGallery as img, i}
        <button
          type="button"
          class="thumb"
          aria-label={"Open image: " + img.alt}
          on:click={() => openLB(i)}
        >
          <img src={img.src} alt={img.alt} loading="lazy" decoding="async" />
        </button>
      {/each}
    </section>
  </main>

  <Footer />
</div>

{#if lbOpen}
  <div
    class="lb-root"
    role="dialog"
    aria-modal="true"
    aria-label="Image viewer"
  >
    <!-- Backdrop is a real button (no self-closing tag) -->
    <button
      class="lb-backdrop"
      type="button"
      aria-label="Close image viewer"
      on:click={closeLB}
    ></button>

    <!-- Dialog content -->
    <div
      class="lb-content"
      role="document"
      on:pointerdown|stopPropagation
    >
      <button
        class="lb-close"
        type="button"
        aria-label="Close image"
        on:click={closeLB}
      >×</button>

      <img
        class="lb-image"
        src={proGallery[lbIndex].src}
        alt={proGallery[lbIndex].alt}
      />
    </div>
  </div>
{/if}







<style>
  /* Page skeleton: header / content / footer */
  .page {
    min-height: 100svh;
    display: grid;
    grid-template-rows: auto 1fr auto;
  }

  /* Match your global look */
  :global(html) { scroll-behavior: smooth; }
  :global(body) {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }

  .section { padding: 4rem 1.25rem; }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    place-items: center;
  }

  .intro-text {
    max-width: 760px;
    
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

  .cta a {
    text-decoration: none;
    font-weight: 600;
    color: inherit;
    transition: opacity 0.2s ease;
  }
  .cta a:hover { opacity: 0.8; }

  /* ====== New gallery ====== */
  .pro-gallery {
    margin: 3rem auto 0;
    max-width: 1200px;
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: nowrap; /* single row on desktop */
  }

  .thumb {
    padding: 0;
    border: none;
    background: transparent;
    cursor: pointer;
    border-radius: 12px;
    overflow: hidden;
    display: block;
    flex: 0 1 360px;           /* responsive width per item */
    max-width: 32%;            /* keeps three across */
  }
  .thumb:focus { outline: none; }
  .thumb:focus-visible {
    outline: 2px solid rgba(0, 102, 255, 0.65);
    outline-offset: 3px;
  }
  .thumb img {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 12px;
    transition: transform 180ms ease;
  }
  .thumb img:hover { transform: scale(1.02); }

  /* Mobile: stack in a centered column */
  @media (max-width: 800px) {
    .pro-gallery {
      flex-wrap: wrap;
      gap: 0.75rem;
      padding-inline: 1rem;
    }
    .thumb {
      max-width: 520px;
      width: 100%;
      flex: 1 1 100%;
      margin-inline: auto;
    }
  }

  /* ====== Lightbox ====== */
  /* Lightbox root: non-interactive; holds backdrop + content */
.lb-root {
  position: fixed;
  inset: 0;
  z-index: 999;
  display: grid;
  place-items: center;
  padding: 1rem;
}

/* Full-screen backdrop is a BUTTON (interactive, keyboard-friendly) */
.lb-backdrop {
  all: unset;                /* remove default button styles */
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.7);
  cursor: pointer;
}

/* Content pane */
.lb-content {
  position: relative;
  max-width: min(92vw, 1400px);
  max-height: 90vh;
  display: grid;
  place-items: center;
}

/* Image */
.lb-image {
  max-width: 100%;
  max-height: 88vh;
  width: auto;
  height: auto;
  object-fit: contain;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.35);
}

/* Close button */
.lb-close {
  position: absolute;
  top: -0.75rem;
  right: -0.75rem;
  width: 36px;
  height: 36px;
  border-radius: 999px;
  border: none;
  background: rgba(255,255,255,0.95);
  box-shadow: 0 4px 16px rgba(0,0,0,0.25);
  font-size: 1.2rem;
  cursor: pointer;
}

</style>
