<!-- src/Navbar.svelte -->
<script>
  import { push } from 'svelte-spa-router';
  let active = "Home";

  function navigate(path) {
    push(path);
    active = path;
  }
</script>

<style>
  nav {
    display: flex;
    justify-content: space-around;
    background-color: #333;
    padding: 1rem;
  }

  a {
    color: white;
    text-decoration: none;
    font-weight: bold;
  }

  a.active {
    color: #f5c842;
  }
</style>

<nav>
  <a href="/" class:active="{active === 'Home'}" on:click|preventDefault="{() => navigate('/')}">Home</a>
  <a href="/sales" class:active="{active === '/sales'}" on:click|preventDefault="{() => navigate('/sales')}">Sales</a>
  <a href="#" class:active="{active === '/about'}" on:click|preventDefault="{() => navigate('/about')}">About</a>
  <a href="#" class:active="{active === '/contact'}" on:click|preventDefault="{() => navigate('/contact')}">Contact</a>
</nav>
