<script>
  import Home from './home/+page.svelte';
  import { onMount } from 'svelte';

  let scrolled = false;

  const handleScroll = () => {
    if (!scrolled) {
      scrolled = true;
      const target = document.querySelector('.hero-bottom');
      if (target) {
        target.scrollIntoView({ behavior: 'smooth' });
      }
    }
  };

  onMount(() => {
    window.addEventListener('scroll', handleScroll, { once: true });
  });
</script>

<Home />

