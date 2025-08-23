<!-- src/routes/+page.svelte -->

<section class="hero">
  <div class="hero-top">
    <!-- Main logo overlay on top of background -->
    <img class="hero-title" src="/light.png" alt="Solypsa Logo" />
  </div>

  <div class="hero-bottom">
    <div class="byline">
      Precision. Depth. Design. <em>Solypsa</em>
    </div>

    <div class="content">
      <div class="text">
        <!-- optional intro copy -->
      </div>
      <div class="links">
        <a href="/hifi">HI-FI →</a>
        <a href="/pro">PRO →</a>
      </div>
    </div>
  </div>
</section>

<style>
  /* ---------- Global resets (Svelte-safe :global usage) ---------- */
  :global(html) {
    margin: 0;
    padding: 0;
  }
  :global(body) {
    margin: 0;
    padding: 0;
    overflow-x: hidden;
    font-family: 'Inter', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }
  :global(*),
  :global(*::before),
  :global(*::after) {
    box-sizing: border-box;
  }

  /* ---------- Hero layout ---------- */
  .hero {
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  /* Top ~70%, bottom ~30% via flex ratios */
  .hero-top {
    flex: 7 0 0;
    position: relative;
    background: url('/nnnn.png') center / cover no-repeat;
  }

  /* Centered logo */
  .hero-title {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    max-width: 40%;
    height: auto;
    opacity: 0;
    animation: fadeIn 2s ease-in-out forwards;
    filter: drop-shadow(0 2px 10px rgba(0,0,0,0.7));
  }

  .hero-bottom {
    flex: 3 0 0;
    background-color: #111;
    color: #fff;
    padding: 1rem 1.5rem;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;   /* centers the byline container horizontally */
  }

  .byline {
    font-size: 2rem;
    font-weight: 300;
    font-family: 'Helvetica Neue', sans-serif;
    text-shadow: 0 2px 6px rgba(0,0,0,0.6);
    margin: 0 0 2rem 0;
    text-align: center;    /* ensure centered text */
    width: 100%;
  }

  .content {
    max-width: 1200px;
    width: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 2rem;
  }

  .text {
    flex: 1;
    min-width: 280px;
  }

  .links {
    display: flex;
    gap: 2rem;
    justify-content: center;
    align-items: center;
    font-family: 'Helvetica', sans-serif;
    font-size: 1.5rem;
    text-transform: uppercase;
  }

  .links a {
    color: #fff;
    text-decoration: none;
    padding: 0.25rem 0;
    border-bottom: 2px solid transparent;
    transition: border-color 0.2s;
  }

  .links a:hover {
    border-color: #fff;
  }

  /* ---------- Responsive ---------- */
  @media (max-width: 768px) {
    .byline {
      font-size: 1.8rem;
      padding-inline: 1rem;  /* adds breathing room on very small screens */
      margin-left: auto;      /* hard-center insurance */
      margin-right: auto;
      text-align: center;
    }
    .links {
      flex-direction: column;
    }
    .hero-title {
      max-width: 70%;
    }
  }

  /* ---------- Animations ---------- */
  @keyframes fadeIn {
    from { opacity: 0; transform: translate(-50%, -60%); }
    to   { opacity: 1; transform: translate(-50%, -50%); }
  }
</style>

