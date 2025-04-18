<script>
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';

	let mapLoaded = false;

	onMount(() => {
		// Simuliamo il caricamento per effetti visivi
		const observer = new IntersectionObserver(
			(entries) => {
				if (entries[0].isIntersecting) {
					mapLoaded = true;
					observer.disconnect();
				}
			},
			{ threshold: 0.1 }
		);

		const el = document.getElementById('map-container');
		if (el) observer.observe(el);
	});
</script>

<section id="map-container" class="flex w-full flex-col items-center px-6 py-12">
	<h2 class="mb-4 text-lg font-semibold">Location Map</h2>
	{#if mapLoaded}
		<div in:fade={{ duration: 1000 }} class="w-full max-w-[360px]">
			<div class="rounded-xl bg-white p-2">
				<iframe
					src="https://maps.google.com/maps?q=Viale+Carlo+Ceppi+5+10126+Torino+TO&z=15&output=embed"
					width="100%"
					height="300"
					style="border:0;"
					allowfullscreen=""
					loading="lazy"
					referrerpolicy="no-referrer-when-downgrade"
					title="Villa Glicini Location"
					class="rounded-lg"
				></iframe>
			</div>
		</div>
	{:else}
		<div class="flex h-72 w-full max-w-[360px] items-center justify-center rounded-xl bg-gray-100">
			<div class="text-gray-400">Caricamento mappa...</div>
		</div>
	{/if}
</section>
