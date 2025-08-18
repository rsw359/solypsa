<script>
  const year = new Date().getFullYear();
</script>

<!-- svelte-ignore a11y_no_redundant_roles -->
<footer class="site-footer" role="contentinfo">
  <div class="footer-inner">
    <div class="footer-left">Site built by Climb Studio</div>
    <div class="footer-center">© {year} Solypsa</div>
    <div class="footer-right">
      <a href="https://instagram.com/solypsa.audio" target="_blank" rel="noopener" aria-label="Instagram" class="insta-link">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 24 24">
          <path d="M12 2.2c3.2 0 3.6 0 4.8.1 1.2.1 2 .2 2.5.4.6.2 1 .4 1.5.9.5.5.7.9.9 1.5.2.5.3 1.3.4 2.5.1 1.2.1 1.6.1 4.8s0 3.6-.1 4.8c-.1 1.2-.2 2-.4 2.5-.2.6-.4 1-.9 1.5-.5.5-.9.7-1.5.9-.5.2-1.3.3-2.5.4-1.2.1-1.6.1-4.8.1s-3.6 0-4.8-.1c-1.2-.1-2-.2-2.5-.4-.6-.2-1-.4-1.5-.9-.5-.5-.7-.9-.9-1.5-.2-.5-.3-1.3-.4-2.5C2.2 15.6 2.2 15.2 2.2 12s0-3.6.1-4.8c.1-1.2.2-2 .4-2.5.2-.6.4-1 .9-1.5.5-.5.9-.7 1.5-.9.5-.2 1.3-.3 2.5-.4C8.4 2.2 8.8 2.2 12 2.2m0-2.2C8.7 0 8.3 0 7 .1 5.7.2 4.7.4 3.9.7c-.9.3-1.6.7-2.3 1.4-.7.7-1.1 1.4-1.4 2.3C0 5.3-.2 6.3-.1 7.6 0 9 0 9.3 0 12c0 2.7 0 3 .1 4.4.1 1.3.3 2.3.6 3.1.3.9.7 1.6 1.4 2.3.7.7 1.4 1.1 2.3 1.4.8.3 1.8.5 3.1.6 1.4.1 1.7.1 4.4.1s3 0 4.4-.1c1.3-.1 2.3-.3 3.1-.6.9-.3 1.6-.7 2.3-1.4.7-.7 1.1-1.4 1.4-2.3.3-.8.5-1.8.6-3.1.1-1.4.1-1.7.1-4.4s0-3-.1-4.4c-.1-1.3-.3-2.3-.6-3.1-.3-.9-.7-1.6-1.4-2.3C21.7 1.4 21 1 20.1.7c-.8-.3-1.8-.5-3.1-.6C15 .1 14.7 0 12 0z"/>
          <path d="M12 5.8A6.2 6.2 0 1 0 18.2 12 6.2 6.2 0 0 0 12 5.8zm0 10.2A4 4 0 1 1 16 12a4 4 0 0 1-4 4zM18.4 4.6a1.4 1.4 0 1 0 1.4 1.4 1.4 1.4 0 0 0-1.4-1.4z"/>
        </svg>
        <span>Instagram</span>
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
    z-index: 1000;
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

  .footer-right a {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    color: inherit;
    text-decoration: none;
    transition: transform 0.2s ease, color 0.2s ease;
  }

  .footer-right a:hover {
    color: black;
    transform: scale(1.05);
  }

  .footer-right svg {
    transition: transform 0.2s ease;
  }

  .footer-right a:hover svg {
    transform: scale(1.1);
  }
</style>
