<script>
	import Router from "svelte-spa-router";
	import { wrap } from "svelte-spa-router/wrap";
	import Navbar from "./components/Navbar.svelte";
	import Company from "./pages/company/Company.svelte";
	import NotFound from "./pages/Notfound.svelte";
	let token = localStorage.getItem("token");
	let routes = "";
	let isNav = false;
	token = "123123123"
	if (token == "" || token == null) {
		routes = {
			"/": wrap({
				component: Login,
			}),
			"*": NotFound,
		};
	} else {
		isNav = true;
		routes = {
			"/": wrap({
				component: Company,
			}),
			"*": NotFound,
		};
	}
</script>

{#if isNav}
	<Navbar />
{/if}
<Router {routes} />
