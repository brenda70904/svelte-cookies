<script>
	import Router from "svelte-spa-router";
	import Navbar from "./Navbar.svelte";
	import Hero from "./Hero.svelte";
	import Sales from "./Sales.svelte";

	const routes = {
  '/': Hero,
  '/sales': Sales,
};
</script>


<Navbar />
<main>
<Router {routes}/>
</main>


