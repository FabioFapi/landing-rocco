<!-- src/lib/components/Countdown.svelte -->
<script>
	import { onMount, onDestroy } from 'svelte';
	export let target;
	export let bgSrc = '';

	let days = '18';
	let hours = '03';
	let minutes = '27';
	let seconds = '00';
	let interval;

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

		days = pad(d);
		hours = pad(h);
		minutes = pad(m);
		seconds = pad(s);
	}

	onMount(() => {
		updateCountdown();
		interval = setInterval(updateCountdown, 1000);
	});

	onDestroy(() => {
		clearInterval(interval);
	});
</script>

<section class="flex w-full justify-center py-8">
	<div
		class="flex w-full max-w-[360px] items-center justify-between rounded-full bg-cover bg-center px-6 py-3"
		style="background-image: url({bgSrc});"
	>
		<!-- Days -->
		<div class="flex flex-col items-center">
			<div class="font-serif text-3xl font-bold text-black">{days}</div>
			<div class="text-[10px] font-medium tracking-wide text-black uppercase">Days</div>
		</div>

		<div class="text-xl font-bold text-black">:</div>

		<!-- Hours -->
		<div class="flex flex-col items-center">
			<div class="font-serif text-3xl font-bold text-black">{hours}</div>
			<div class="text-[10px] font-medium tracking-wide text-black uppercase">Hours</div>
		</div>

		<div class="text-xl font-bold text-black">:</div>

		<!-- Minutes -->
		<div class="flex flex-col items-center">
			<div class="font-serif text-3xl font-bold text-black">{minutes}</div>
			<div class="text-[10px] font-medium tracking-wide text-black uppercase">Minutes</div>
		</div>

		<div class="text-xl font-bold text-black">:</div>

		<!-- Seconds -->
		<div class="flex flex-col items-center">
			<div class="font-serif text-3xl font-bold text-black">{seconds}</div>
			<div class="text-[10px] font-medium tracking-wide text-black uppercase">Seconds</div>
		</div>
	</div>
</section>
