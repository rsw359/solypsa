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
  /* ========== Global Styles ========== */
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

  :global(html), :global(body) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    overflow-x: hidden;
    font-family: 'Inter', sans-serif;
    background-color: #eef1f2;
    color: #222;
    line-height: 1.5;
  }

  /* ========== Hero Layout ========== */
  .hero {
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  /* Hero Top fills ~70%, Hero Bottom ~30% */
  .hero-top {
    flex: 7 0 0;
    position: relative;
    background: url('/nnnn.png') center/cover no-repeat;
  }

  /* Centered Logo */
  .hero-title {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    max-width: 40%;
    height: auto;
    opacity: 0;
    animation: fadeIn 2s ease-in-out forwards;
    filter: drop-shadow(0 2px 10px rgba(0, 0, 0, 0.7));
  }

  .hero-bottom {
    flex: 3 0 0;
    background-color: #111;
    color: white;
    padding: 1rem 1.5rem;
    width: 100%;
  }

  .byline {
    font-size: 2rem;
    font-weight: 300;
    text-align: center;
    font-family: 'Helvetica Neue', sans-serif;
    text-shadow: 0 2px 6px rgba(0, 0, 0, 0.6);
    margin-bottom: 2rem;
  }

  .content {
    max-width: 1200px;
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
    color: white;
    text-decoration: none;
    padding: 0.25rem 0;
    border-bottom: 2px solid transparent;
    transition: border-color 0.2s;
  }

  .links a:hover {
    border-color: white;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .byline {
      font-size: 1.8rem;
      padding: 0 1rem;
    }
    .links {
      flex-direction: column;
    }
    .hero-title {
      max-width: 70%;
    }
  }

  /* Animations */
  @keyframes fadeIn {
    from { opacity: 0; transform: translate(-50%, -60%); }
    to   { opacity: 1; transform: translate(-50%, -50%); }
  }
</style>
