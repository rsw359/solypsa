<script>
  import { onMount } from 'svelte';
  let time = '';

  function updateTime() {
    const now = new Date();
    time = now.toLocaleTimeString('en-GB', { hour12: false });
  }

  onMount(() => {
    updateTime();
    const interval = setInterval(updateTime, 1000);
    return () => clearInterval(interval);
  });
</script>

<nav class="header">
  <div class="left"><a href="/home">
  
    <img id="logo-sm" src="/dark1.png" alt="">
  </a>
  </div>

  <div class="center">
    <a href="/nnnn">NNNN →</a>
    <a href="/ethos">RADA →</a>
    <a href="/contact">Audio Creative →</a>
  </div>
  <div class="center">
    <a href="/pro">STST →</a>
    <a href="/ethos">Primary Control→</a>
    <a href="/contact">Contact →</a>
  </div>

  <div class="center">
    <a href="/pro">Ethos →</a>
    <a href="/ethos">Contact →</a>
    
  </div>

  <div class="right">
    <div class="locations">
      <div>Seattle, USA</div>
      
    </div>
    <div class="time">{time}</div>
  </div>
</nav>

<style>
  .header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding: 1rem 2rem;
    background: #eef1f2;
    font-family: 'Helvetica Neue', sans-serif;
    font-weight: 400;
    font-size: 0.9rem;
  }

  .left {
    flex: 1;
    font-size: 1.25rem;
    font-weight: 500;
  }

  #logo-sm {
    height: 50px;
  }

  .center {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    
  }

  .center a {
    text-decoration: none;
    color: black;
    position: relative;
  }

  .right {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 0.25rem;
  }

  .locations {
    text-align: right;
    line-height: 1.2;
  }

  .time {
    font-weight: bold;
  }

  

  @media (max-width: 768px) {
    .header {
      flex-direction: column;
      align-items: flex-start;
      gap: 1rem;
    }

    .center {
      justify-content: flex-start;
      flex-wrap: wrap;
    }

    .right {
      align-items: flex-start;
    }
  }
</style>
