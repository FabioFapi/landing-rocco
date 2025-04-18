<!-- src/lib/components/Countdown.svelte -->
<script>
	import { onMount, onDestroy } from 'svelte';
	import { fly, scale, fade } from 'svelte/transition';
	import { cubicOut, elasticOut } from 'svelte/easing';

	export let target;
	export let bgSrc = '';

	let days = '18';
	let hours = '03';
	let minutes = '27';
	let seconds = '00';
	let interval;
	let visible = false;
	let previousSeconds = '';

	function pad(value) {
		return String(value).padStart(2, '0');
	}

	function updateCountdown() {
		const now = new Date();
		const diff = target - now;

		if (diff <= 0) {
			clearInterval(interval);
			days = hours = minutes = seconds = '00';
			return;
		}

		const d = Math.floor(diff / (1000 * 60 * 60 * 24));
		const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
		const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
		const s = Math.floor((diff % (1000 * 60)) / 1000);

		previousSeconds = seconds;
		days = pad(d);
		hours = pad(h);
		minutes = pad(m);
		seconds = pad(s);
	}

	onMount(() => {
		updateCountdown();
		interval = setInterval(updateCountdown, 1000);
		// Mostra il countdown con un'animazione all'avvio
		setTimeout(() => {
			visible = true;
		}, 300);
	});

	onDestroy(() => {
		clearInterval(interval);
	});
</script>

<section class="flex w-full justify-center py-8" style="font-family: 'Garamond', serif;">
	{#if visible}
		<div
			class="countdown-container flex w-full max-w-[360px] items-center justify-between rounded-full bg-cover bg-center px-6 py-3"
			style="background-image: url({bgSrc});"
			in:scale={{ start: 0.6, duration: 800, easing: elasticOut }}
		>
			<!-- Days -->
			<div class="flex flex-col items-center" in:fly={{ y: 20, duration: 600, delay: 100 }}>
				{#key days}
					<div
						class="number-display font-serif text-3xl font-bold text-black"
						in:scale={{ duration: 300, start: 0.8, easing: cubicOut }}
					>
						{days}
					</div>
				{/key}
				<div class="text-[10px] font-medium tracking-wide text-black uppercase">Days</div>
			</div>

			<div class="pulse text-xl font-bold text-black">:</div>

			<!-- Hours -->
			<div class="flex flex-col items-center" in:fly={{ y: 20, duration: 600, delay: 200 }}>
				{#key hours}
					<div
						class="number-display font-serif text-3xl font-bold text-black"
						in:scale={{ duration: 300, start: 0.8, easing: cubicOut }}
					>
						{hours}
					</div>
				{/key}
				<div class="text-[10px] font-medium tracking-wide text-black uppercase">Hours</div>
			</div>

			<div class="pulse text-xl font-bold text-black">:</div>

			<!-- Minutes -->
			<div class="flex flex-col items-center" in:fly={{ y: 20, duration: 600, delay: 300 }}>
				{#key minutes}
					<div
						class="number-display font-serif text-3xl font-bold text-black"
						in:scale={{ duration: 300, start: 0.8, easing: cubicOut }}
					>
						{minutes}
					</div>
				{/key}
				<div class="text-[10px] font-medium tracking-wide text-black uppercase">Minutes</div>
			</div>

			<div class="pulse text-xl font-bold text-black">:</div>

			<!-- Seconds -->
			<div class="flex flex-col items-center" in:fly={{ y: 20, duration: 600, delay: 400 }}>
				{#key seconds}
					<div
						class="number-display seconds-display font-serif text-3xl font-bold text-black"
						in:scale={{ duration: 300, start: 0.8, easing: cubicOut }}
					>
						{seconds}
					</div>
				{/key}
				<div class="text-[10px] font-medium tracking-wide text-black uppercase">Seconds</div>
			</div>
		</div>
	{/if}
</section>

<style>
	.countdown-container {
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
		transition:
			transform 0.3s ease,
			box-shadow 0.3s ease;
	}

	.countdown-container:hover {
		transform: translateY(-5px);
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
	}

	.number-display {
		transition: color 0.3s ease;
	}

	.seconds-display {
		position: relative;
	}

	@keyframes pulse {
		0% {
			opacity: 1;
		}
		50% {
			opacity: 0.5;
		}
		100% {
			opacity: 1;
		}
	}

	.pulse {
		animation: pulse 1s infinite;
	}

	.number-display:hover {
		color: #ff6b6b;
	}
</style>
