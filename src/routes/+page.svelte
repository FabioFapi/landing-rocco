<script>
	import Hero from '$lib/components/Hero.svelte';
	import Countdown from '$lib/components/Countdown.svelte';
	import CenteredText from '$lib/components/CenteredText.svelte';
	import EventInfo from '$lib/components/EventInfo.svelte';
	import RegistrationForm from '$lib/components/RegistrationForm.svelte';
	import MapEmbed from '$lib/components/MapEmbed.svelte';

	let heroImage = '/images/hero.jpg';
	let heroAlt = 'Banner evento';
	let bgImage = '/images/gradient.jpg';
	let targetDate = new Date('2025-05-17T20:00:00');
</script>

<main class="container mx-auto max-w-md space-y-8">
	<!-- Hero -->
	<Hero src={heroImage} alt={heroAlt} />
	<div class="flex w-full justify-center">
		<div class="w-full max-w-[320px] px-4">
			<Countdown target={targetDate} bgSrc={bgImage} />
		</div>
	</div>
	<CenteredText />
	<EventInfo />
	<RegistrationForm />
	<MapEmbed />
</main>

<style>
	main {
		font-family: 'Montserrat', sans-serif;
	}
</style>
