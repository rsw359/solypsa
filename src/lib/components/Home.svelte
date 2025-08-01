
<!-- src/lib/components/Home.svelte -->
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
        <!-- <p>
          At Solypsa, we bring analog excellence into focus — through carefully curated
          audio equipment and thoughtful design.
        </p> -->
      </div>
      <div class="links">
        <a href="/hifi">Hi‑FI</a>
        
        <a href="/pro">PRO</a>
      </div>
    </div>
  </div>
</section>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

  :global(body), :global(html) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background-color: #000;
  }

  .hero {
    display: flex;
    flex-direction: column;
    width: 100%;
    overflow-x: hidden;
  }

  .hero-top {
    position: relative;
    height: 70vh;                    /* shorter than a full viewport */
    background: url('/nnnn.png') center/cover no-repeat; /* pastel placeholder */
  }

  .byline {
    font-size: 2rem;
    font-weight: 300;
    color: white;
    text-align: center;
    font-family: 'Helvetica Neue', sans-serif;
    text-shadow: 0 2px 6px rgba(0,0,0,0.6);
  }

  .hero-bottom {
    height: 25vh; /* remaining height */
    background-color: #111;
    color: white;
    padding: 1rem 1.5rem;
    width: 100%;
  }

  .content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;   /* stack text and links */
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
  font-family: 'Barlow', sans-serif;
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
  border-color: white;       /* underline on hover for a subtle cue */
}

  @media (max-width: 768px) {
    .byline { font-size: 1.8rem; padding: 0 1rem; }
    .content { flex-direction: column; text-align: center; }
    .links { flex-direction: column; align-items: center; }
  }

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

  @keyframes fadeIn {
    from { opacity: 0; transform: translate(-50%, -60%); }
    to   { opacity: 1; transform: translate(-50%, -50%); }
  }
</style>
