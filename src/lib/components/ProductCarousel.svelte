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

  // Lightbox state
  let lightboxOpen = false;
  let lightboxImages = [];
  let lightboxIndex = 0;

  function openLightbox(images, i) {
    if (!images?.length) return;
    lightboxImages = images;
    lightboxIndex = i ?? 0;
    lightboxOpen = true;
  }
  function closeLightbox() { lightboxOpen = false; }

  // Key handling
  function handleKeydown(e) {
    // Lightbox: only Esc handled here
    if (lightboxOpen) {
      if (e.key === 'Escape') { e.preventDefault(); closeLightbox(); }
      return;
    }
    // Slides: only when active
    if (!isActive) return;
    if (e.key === 'ArrowRight') { e.preventDefault(); next(); }
    if (e.key === 'ArrowLeft')  { e.preventDefault(); prev(); }
  }

  // Backdrop keyboard close for a11y
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
  <div class="track-wrapper">
    <div class="track" style="--index:{index};">
      {#each products as p, i (p.id)}
        <article class="slide" aria-hidden={index !== i}>
          <div class="slide-inner">
            <!-- Text column -->
            <div class="text">
              <h3>{p.title}</h3>
                  {#if p.copy}<p>{@html p.copy}</p>{/if}
                  {#if p.link?.url}
                    <p class="product-link">
                      <a href={p.link.url} target="_blank" rel="noopener noreferrer">
                        {p.link.label ?? 'Learn more →'}
                      </a>
                    </p>
      {/if}

      {#if total() > 1}
        <nav class="slide-controls" aria-label="Slide controls">
          <button class="ctrl-btn" type="button" on:click={prev} aria-label="Previous slide">←</button>
          <div class="ctrl-indicator" aria-live="polite">{index + 1} / {total()}</div>
          <button class="ctrl-btn" type="button" on:click={next} aria-label="Next slide">→</button>
        </nav>
      {/if}
    </div>


           

            <!-- Gallery / Thumbs -->
            {#if p.images && p.images.length}
              <div class="thumb-grid {p.images.length === 1 ? 'single' : ''}">
                {#each p.images as img, j}
                  <button
                    class="thumb"
                    aria-label={"Open image " + (j+1) + " of " + p.title}
                    on:click={() => openLightbox(p.images, j)}
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
    overflow: hidden;
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
  }

  /* Adjusted padding for tighter vertical rhythm */
  .slide { padding: 2rem 1rem 1.5rem; }

  .slide-inner {
    display: grid;
    grid-template-columns: 1.1fr 1fr;
    gap: var(--gutter);
    align-items: start;
  }

  /* ===== Typography ===== */
  .text {
    font-family: 'Helvetica Neue', Arial, sans-serif;
    font-weight: 300;
  }
  .text h3 {
    font-size: 1.6rem;
    font-weight: 500;
    margin: 0 0 1rem 0;
  }
  .text p {
    margin: 0 0 0.75rem 0;  /* consistent spacing instead of <br><br> */
    line-height: 1.6;
    max-width: 60ch;
    font-weight: 300;
    text-align: justify;
  }

  .product-link a {
    text-decoration: none;
    font-weight: 400;
    color: inherit;
    transition: opacity 0.2s ease;
  }
  .product-link a:hover { opacity: 0.8; }

  /* ===== Slide controls inside text ===== */
  .text .slide-controls {
    margin-top: 0.75rem;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: 0.5rem;
    padding-right: 0;
  }
  /* Flat, text-only controls */
.ctrl-btn {
  justify-self: start;           /* keep your left/right alignment logic */
  appearance: none;
  background: transparent;       /* no background */
  border: none;                  /* no border */
  box-shadow: none;              /* no shadow */
  border-radius: 0;              /* no pill shape */

  padding: 0.25rem 0.5rem;       /* keep a decent hit area */
  width: auto;                   /* shrink-wrap the arrow glyph */
  height: auto;
  cursor: pointer;

  font-size: 1.25rem;            /* arrow size */
  line-height: 1;
  color: inherit;                /* match surrounding text color */
}

.ctrl-btn:hover { opacity: 0.75; }

.ctrl-btn:focus { outline: none; }
.ctrl-btn:focus-visible {
  outline: 2px solid rgba(0, 102, 255, 0.65);
  outline-offset: 3px;
}

  .ctrl-btn:last-child { justify-self: end; }
  .ctrl-btn:focus-visible {
    outline: 3px solid rgba(0, 102, 255, 0.6);
    outline-offset: 2px;
  }
  .ctrl-indicator { font-size: 0.9rem; }

  /* ===== Thumbnails ===== */
  .thumb-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(140px, 1fr));
    gap: 0.75rem;
    justify-content: center;
    justify-items: center;
    align-items: start;
    width: 100%;
    max-width: 620px;
    margin: 0 auto;
  }
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
  .thumb img {
    display: block;
    width: 100%;
    height: auto;
    border-radius: 10px;
    transition: transform 180ms ease;
    background-color: #eef1f2; /* unify PNGs with bg */
  }
  .thumb img:hover { transform: scale(1.03); }

  /* ===== Lightbox ===== */
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
    max-height: 88vh;
    width: auto;
    height: auto;
    object-fit: contain;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.35);
    background-color: #eef1f2;
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
    .slide-inner {
      grid-template-columns: 1fr;
      gap: 1.25rem;
      text-align: justify;
    }
  }
  @media (max-width: 520px) {
    .slide { padding: 2rem 1rem 1.5rem; }
    .thumb-grid { grid-template-columns: repeat(2, minmax(120px, 1fr)); max-width: 520px; }
    .lb-close { top: 0.5rem; right: 0.5rem; }
  }

  /* Reduced motion */
  @media (prefers-reduced-motion: reduce) {
    .track { transition: none; }
    .thumb img { transition: none; }
  }
</style>

