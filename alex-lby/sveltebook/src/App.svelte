<script>
	
	import {  Products, Product, Header, Footer, CartLength, Cart } from "./components";
	import About from "./pages/About.svelte";
	import Home from "./pages/Home.svelte";
	import Coffee from './pages/Coffee.svelte';

	import { Router, Link, Route } from "svelte-routing";
	// import { products, cart, counter } from "./stores";

	export let url = "";
	export let name;
	

</script>

<Header/>

<Router url="{url}">

	<nav>
		<Link to="/">Home</Link>
		<Link to="/products">Shop</Link>
		<Link to="/about">Our Story</Link>
		<Link to="/coffee">Our Coffee</Link>
	</nav>

	<main>
		<Route path="/" component="{Home}" />
		<Route path="products" component="{Products}" />
		<Route path="about" component="{About}" />
		<Route path="coffee" component="{Coffee}" />
		<Route path="/product/:id" component="{Product}" />
	</main>


</Router>

<Footer />


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}



	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>