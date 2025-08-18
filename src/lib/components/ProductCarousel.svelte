<script>
  export let products = [];

  // Slide state
  let index = 0;
  const total = () => products.length;
  const clamp = (n) => (n + total()) % total();
  const go   = (i) => (index = clamp(i));
  const next = () => go(index + 1);
  const prev = () => go(index - 1);

  // Activate keyboard nav only when user interacts with the carousel
  let root;
  let isActive = false;
  const activate = () => (isActive = true);
  const deactivate = () => (isActive = false);

  // Swipe between slides
  let startX = 0, deltaX = 0;
  const SWIPE = 50;
  const onTouchStart = (e) => { startX = e.touches[0].clientX; deltaX = 0; activate(); };
  const onTouchMove  = (e) => { deltaX = e.touches[0].clientX - startX; };
  const onTouchEnd   = () => {
    if (Math.abs(deltaX) > SWIPE) (deltaX < 0 ? next() : prev());
    startX = 0; deltaX = 0; deactivate();
  };

  // Global key handler (slides only; lightbox handled separately)
  let lightboxOpen = false;
  let lightboxImages = [];
  let lightboxIndex = 0;

  const handleKeydown = (e) => {
    if (lightboxOpen) {
      if (e.key === 'Escape') { e.preventDefault(); closeLightbox(); }
      return;
    }
    if (!isActive) return;
    if (e.key === 'ArrowRight') { e.preventDefault(); next(); }
    if (e.key === 'ArrowLeft')  { e.preventDefault(); prev(); }
  };

  // Lightbox
  function openLightbox(images, i) {
    if (!images?.length) return;
    lightboxImages = images;
    lightboxIndex = i ?? 0;
    lightboxOpen = true;
  }
  function closeLightbox() { lightboxOpen = false; }

  // Backdrop keyboard close (dialog must react to keys if it has click)
  const handleBackdropKey = (e) => {
    if (!lightboxOpen) return;
    if (e.key === 'Escape' || e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      closeLightbox();
    }
  };
</script>

<svelte:window on:keydown={handleKeydown} />

<section
  bind:this={root}
  class="carousel"
  aria-label="Product carousel"
  on:focusin={() => activate()}
  on:focusout={(e) => { if (!root?.contains?.(e.relatedTarget)) deactivate(); }}
  on:mouseenter={() => activate()}
  on:mouseleave={() => deactivate()}
  on:touchstart={onTouchStart}
  on:touchmove={onTouchMove}
  on:touchend={onTouchEnd}
>
  <!-- Slides -->
  <div class="track-wrapper">
    <div class="track" style="--index:{index};">
      {#each products as p (p.id)}
        <article class="slide">
          <div class="slide-inner">
            <div class="text">
              <h3>{p.title}</h3>
              {#if p.copy}
                <p>{@html p.copy}</p>
              {/if}
              {#if p.link?.url}
    <p class="product-link">
      <a href={p.link.url} target="_blank" rel="noopener noreferrer">
        {p.link.label ?? 'Learn more →'}
      </a>
    </p>
  {/if}
            </div>



            {#if p.images && p.images.length}
              <!-- Thumbnails: 2×2; odd last centers on new row -->
              <div class="thumb-grid {p.images.length === 1 ? 'single' : ''}">
                {#each p.images as img, i}
                  <button
                    class="thumb"
                    aria-label={"Open image " + (i+1) + " of " + p.title}
                    on:click={() => openLightbox(p.images, i)}
                    type="button"
                  >
                    <img src={img.src} alt={img.alt} loading="lazy" decoding="async" />
                  </button>
                {/each}
              </div>
            {/if}
          </div>
        </article>
      {/each}
    </div>
  </div>

  <!-- Carousel arrows -->
  {#if total() > 1}
    <button class="carousel-arrow left" on:click={prev} aria-label="Previous slide" type="button">‹</button>
    <button class="carousel-arrow right" on:click={next} aria-label="Next slide" type="button">›</button>
  {/if}
</section>

{#if lightboxOpen}
  <div
    class="lb-backdrop"
    role="dialog"
    aria-modal="true"
    aria-label="Image viewer"
    tabindex="-1"
    on:click={closeLightbox}
    on:keydown={handleBackdropKey}
  >
    <!-- stop inside clicks from closing -->
    <div class="lb-content" on:pointerdown|stopPropagation>
      <button class="lb-close" aria-label="Close image" on:click={closeLightbox} type="button">×</button>

      <img
        class="lb-image"
        src={lightboxImages[lightboxIndex].src}
        alt={lightboxImages[lightboxIndex].alt}
      />
    </div>
  </div>
{/if}

<style>
  /* ===== Base layout ===== */
  .carousel {
    --gutter: 2rem;
    --max: 1200px;
    position: relative;
    outline: none;
  }
  .track-wrapper {
    overflow: hidden;            /* hide off-screen slides */
    width: 100%;
    max-width: var(--max);
    margin: 0 auto;
  }
  .track {
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 100%;
    transform: translateX(calc(var(--index) * -100%));
    transition: transform 320ms ease;
    /* width: 100%;
    max-width: none; */
  }
  .slide { padding: 3rem 1rem; }
  .slide-inner {
    display: grid;
    grid-template-columns: 1.1fr 1fr;
    gap: var(--gutter);
    align-items: start;
  }

  /* ===== Typography (reverted weights) ===== */
  .text {
    font-family: 'Helvetica Neue', Arial, sans-serif;
    font-weight: 300;            /* ← revert to your original light body */
  }
  .text h3 {
    font-size: 1.6rem;
    font-weight: 500;            /* ← revert to semi-bold heading as before */
    margin: 0 0 1rem 0;
  }
  .text p {
    margin: 0;
    line-height: 1.6;
    max-width: 60ch;
    font-weight: 300;            /* ensure copy remains light */
  }
  
  .product-link a {
    text-decoration: none;   /* no underline */
    font-weight: 400;        /* stronger than normal (use 700 for boldest) */
    color: inherit;          /* matches the surrounding text color */
    transition: opacity 0.2s ease;
  }

  .product-link a:hover {
    opacity: 0.8;            /* subtle feedback on hover */
  }
  /* ===== Thumbnails (no borders) ===== */
  .thumb-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(140px, 1fr));
    gap: 0.75rem;
    justify-content: center;   /* center the overall grid */
    justify-items: center;     /* center items within cells */
    align-items: start;
    width: 100%;
    max-width: 620px;
    margin: 0 auto;
  }
  /* If odd count, center the last one on its own row */
  .thumb-grid > .thumb:last-child:nth-child(odd) {
    grid-column: 1 / -1;
    justify-self: center;
  }
  .thumb-grid.single { grid-template-columns: 1fr; max-width: 420px; }

  .thumb {
    padding: 0;
    border: none;
    background: transparent;
    cursor: pointer;
    border-radius: 10px;
    overflow: hidden;
  }
  .thumb:focus { outline: none; }
  .thumb:focus-visible {
    outline: 2px solid rgba(0, 102, 255, 0.65);
    outline-offset: 3px;
  }
  .thumb img {
    display: block;
    width: 100%;
    height: auto;
    border: none;    /* remove any UA image borders */
    outline: none;   /* prevent UA outlines */
    border-radius: 10px;
    transition: transform 180ms ease;
  }
  .thumb img:hover { transform: scale(1.03); }

  /* ===== Carousel arrows (side-centered) ===== */
 /* ===== Carousel arrows (side-centered) ===== */
.carousel-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255,255,255,0.9);
  border: none;
  border-radius: 999px;
  width: 48px;
  height: 48px;
  cursor: pointer;
  font-size: 1.6rem;
  line-height: 1;
  box-shadow: 0 4px 16px rgba(0,0,0,0.18);
  z-index: 2; /* ensure above images but below text if needed */
}

/* Nudge arrows inward/outward relative to the max content width */
.carousel-arrow.left {
  left: calc((100vw - var(--max)) / 2 - 2.5rem);
}
.carousel-arrow.right {
  right: calc((100vw - var(--max)) / 2 - 2.5rem);
}

/* Accessibility focus */
.carousel-arrow:focus-visible {
  outline: 3px solid rgba(0, 102, 255, 0.6);
  outline-offset: 2px;
}

/* Mobile adjustments: keep arrows closer in */
@media (max-width: 900px) {
  .carousel-arrow.left  { left: 0.5rem; }
  .carousel-arrow.right { right: 0.5rem; }
}


  /* ===== Lightbox (no arrows) ===== */
  .lb-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    z-index: 999;
    display: grid;
    place-items: center;
    padding: 1rem;
  }
  .lb-content {
    position: relative;
    max-width: min(92vw, 1400px);
    max-height: 90vh;
    display: grid;
    place-items: center;
  }
  .lb-image {
    max-width: 100%;
    max-height: 88vh;           /* cap to viewport height */
    width: auto;
    height: auto;
    object-fit: contain;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.35);
  }
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

  /* ===== Responsive ===== */
  @media (max-width: 900px) {
    .slide-inner { grid-template-columns: 1fr; gap: 1.25rem; text-align: center; }
  }
  @media (max-width: 520px) {
    .slide { padding: 2rem 1rem; }
    .thumb-grid { grid-template-columns: repeat(2, minmax(120px, 1fr)); max-width: 520px; }
    .lb-close { top: 0.5rem; right: 0.5rem; }
  }

  /* Reduced motion */
  @media (prefers-reduced-motion: reduce) {
    .track { transition: none; }
    .thumb img { transition: none; }
  }
</style>
