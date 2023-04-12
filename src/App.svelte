<script>
	import Router from "svelte-spa-router";
	import Navbar from "./Navbar.svelte";
	import Hero from "./Hero.svelte";
	import Details from "./Details.svelte";
	import Sales from "./Sales.svelte";

	const routes = {
  '/': Hero,
  '/sales': Sales,
};
</script>


<style>
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 2rem;
	}
</style>

<Navbar />
<main>
<Router {routes}/>
</main>


