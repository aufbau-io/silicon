<script>
	import '../app.css';
	import { onMount } from 'svelte';
	let Geometry;

	import Header from '$lib/components/header/header.svelte';
	import Footer from '$lib/components/footer/footer.svelte';

	onMount(async () => {
		const module = await import('$lib/components/geometry/Geometry.svelte');
		Geometry = module.default;
	});

	/*
	// important for accessibility
	if (import.meta.env.DEV) {
		onMount(() =>
			import('https://unpkg.com/agnostic-axe@3').then(({ AxeObserver, logViolations }) => {
				const MyAxeObserver = new AxeObserver(logViolations);
				MyAxeObserver.observe(document);
			})
		);
	}*/
</script>

<Header />
<svelte:component this={Geometry} />

<main>
	<slot />
</main>
<Footer />

<style>
	main {
		min-height: calc(100vh - 150px);
	}
</style>
