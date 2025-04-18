<!-- src/lib/components/Hero.svelte -->
<script>
	import { onMount } from 'svelte';
	import { fade, fly, scale } from 'svelte/transition';
	import { spring } from 'svelte/motion';
	
	export let src;
	export let alt = 'Hero image';
	export let title = '';
	export let subtitle = '';
	
	let visible = false;
	
	onMount(() => {
		// Attiva l'animazione dopo il caricamento del componente
		visible = true;
	});
	
	// Spring animation per l'effetto "bounce"
	const scaleValue = spring({ x: 0, y: 0 }, {
		stiffness: 0.1,
		damping: 0.4
	});
	
	// Attiva l'effetto di rimbalzo quando diventa visibile
	$: if (visible) {
		scaleValue.set({ x: 1, y: 1 });
	}
</script>

<section class="relative w-full overflow-hidden">
	{#if visible}
		<!-- Immagine hero con fade in -->
		<div class="w-full">
			<img 
				{src} 
				{alt} 
				class="h-auto w-full object-cover" 
				in:fade={{ duration: 1000, delay: 200 }}
			/>
		</div>
	{/if}
</section>

<style>
	section {
		min-height: 40vh;
	}
	
	img {
		transition: transform 0.5s ease-in-out;
	}
	
	img:hover {
		transform: scale(1.03);
	}
	
	@keyframes fadeIn {
		from { opacity: 0; }
		to { opacity: 1; }
	}
</style>