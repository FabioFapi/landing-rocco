<!-- src/lib/components/Hero.svelte -->
<script>
	export let src;
	export let alt = 'Hero image';
</script>

<section class="relative w-full">
	<!-- Immagine hero -->
	<div class="w-full">
		<img {src} {alt} class="h-auto w-full object-cover" />
	</div>
</section>
