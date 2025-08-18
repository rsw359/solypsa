<script>
  const year = new Date().getFullYear();
</script>

<!-- svelte-ignore a11y_no_redundant_roles -->
<footer class="site-footer" role="contentinfo">
  <div class="footer-inner">
    <div class="footer-left">Site build by Climb Studio</div>
    <div class="footer-center">© {year} Solypsa</div>
    <div class="footer-right">
      <a href="https://instagram.com/solypsa" target="_blank" rel="noopener" aria-label="Instagram">
        Instagram
      </a>
    </div>
  </div>
</footer>

<style>
  .site-footer {
           
    bottom: 0;
    left: 0;
    width: 100%;

    background: transparent;
    z-index: 1000;         /* keep it above page content */
  }

  .footer-inner {
    height: 56px;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;

    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: 1rem;

    font-family: 'Helvetica Neue', sans-serif;
    font-size: 0.9rem;
  }

  .footer-left  { justify-self: start; color: rgba(0,0,0,0.32); font-weight: 300; }
  .footer-center{ justify-self: center; color: rgba(0,0,0,0.32); font-weight: 400; }
  .footer-right { justify-self: end; color: rgba(0,0,0,0.32); font-weight: 400; }
  .footer-right a { color: inherit; text-decoration: none;  }
  .footer-right a:hover { color: black; }
</style>
