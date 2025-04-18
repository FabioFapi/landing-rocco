<script>
	import { onMount } from 'svelte';
	import { fade, fly, slide } from 'svelte/transition';
	import { spring } from 'svelte/motion';

  import '../app.css';
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

	// Per le animazioni sequenziali
	let visible = false;
	let componentVisibility = {
		hero: false,
		countdown: false,
		centeredText: false,
		eventInfo: false,
		registration: false,
		map: false
	};

	// Semplice animazione per l'effetto di scrolling
	function handleScroll() {
		const scrollY = window.scrollY;
		const windowHeight = window.innerHeight;
		const pageHeight = document.body.scrollHeight;

		// Controllo della visibilità di ogni sezione in base allo scroll
		const sections = document.querySelectorAll('section');
		sections.forEach((section, index) => {
			const rect = section.getBoundingClientRect();
			if (rect.top < windowHeight * 0.8) {
				// Imposta la visibilità del componente in base all'indice
				const keys = Object.keys(componentVisibility);
				if (index < keys.length) {
					componentVisibility[keys[index]] = true;
				}
			}
		});
	}

	onMount(() => {
		visible = true;
		componentVisibility.hero = true;

		// Sequenza di animazione iniziale
		setTimeout(() => (componentVisibility.countdown = true), 400);
		setTimeout(() => (componentVisibility.centeredText = true), 800);

		// Aggiungi listener per animazioni basate sullo scroll
		window.addEventListener('scroll', handleScroll);

		return () => {
			window.removeEventListener('scroll', handleScroll);
		};
	});
</script>

<main class="container mx-auto max-w-md space-y-8" in:fade={{ duration: 800, delay: 200 }}>
	<!-- Hero -->
	<section>
		{#if componentVisibility.hero}
			<div in:fade={{ duration: 800 }}>
				<Hero src={heroImage} alt={heroAlt} />
			</div>
		{/if}
	</section>

	<section>
		{#if componentVisibility.countdown}
			<div in:fly={{ y: 20, duration: 800 }}>
				<div class="flex w-full justify-center">
					<div class="w-full max-w-[320px] px-4">
						<Countdown target={targetDate} bgSrc={bgImage} />
					</div>
				</div>
			</div>
		{/if}
	</section>

	<section>
		{#if componentVisibility.centeredText}
			<div in:fly={{ y: 20, duration: 800 }}>
				<CenteredText />
			</div>
		{/if}
	</section>

	<section>
		{#if visible}
			<div
				in:fly={{ y: 20, duration: 800, delay: 200 }}
				class="animate-fadeIn opacity-0"
				style="animation-delay: 1200ms; animation-fill-mode: forwards;"
			>
				<EventInfo />
			</div>
		{/if}
	</section>

	<section>
		{#if visible}
			<div
				in:fly={{ y: 20, duration: 800, delay: 400 }}
				class="animate-fadeIn opacity-0"
				style="animation-delay: 1600ms; animation-fill-mode: forwards;"
			>
				<RegistrationForm />
			</div>
		{/if}
	</section>

	<section>
		{#if visible}
			<div
				in:slide={{ duration: 800, delay: 600 }}
				class="animate-fadeIn opacity-0"
				style="animation-delay: 2000ms; animation-fill-mode: forwards;"
			>
				<MapEmbed />
			</div>
		{/if}
	</section>
</main>

<style>
	main {
		font-family: 'Montserrat', sans-serif;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	.animate-fadeIn {
		animation: fadeIn 0.8s ease-in-out forwards;
	}

	section {
		min-height: 10px;
	}
</style>
