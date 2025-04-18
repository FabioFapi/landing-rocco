<script>
	import { onMount } from 'svelte';
	import { fade, fly, scale } from 'svelte/transition';

	let visible = false;

	onMount(() => {
		// Attiva le animazioni dopo il caricamento
		setTimeout(() => {
			visible = true;
		}, 300);
	});
</script>

<section class="flex w-full justify-center px-6 py-8">
	{#if visible}
		<div
			class="info-card w-full max-w-[360px] space-y-4 text-center text-black"
			in:scale={{ duration: 600, start: 0.9, easing: (t) => --t * t * t + 1 }}
		>
			<h2 class="title-animated text-lg font-semibold" in:fly={{ y: -20, duration: 500 }}>Info</h2>

			<p class="info-item text-base leading-relaxed" in:fly={{ y: 20, duration: 400, delay: 100 }}>
				<span class="emoji-bounce">📅</span> <span class="font-semibold">Date:</span> May 17<sup
					>th</sup
				>, 2025
			</p>
			<p class="info-item text-base leading-relaxed" in:fly={{ y: 20, duration: 400, delay: 200 }}>
				<span class="emoji-bounce">🕓</span> <span class="font-semibold">Time:</span> 8.00 pm
			</p>
			<p class="info-item text-base leading-relaxed" in:fly={{ y: 20, duration: 400, delay: 300 }}>
				<span class="emoji-bounce">📍</span> <span class="font-semibold">Location:</span> Villa Glicini
				Torino
			</p>
			<p class="info-item text-base leading-relaxed" in:fly={{ y: 20, duration: 400, delay: 400 }}>
				<span class="emoji-bounce">🎩</span> <span class="font-semibold">Dress code:</span> Formal elegant
			</p>
		</div>
	{/if}
</section>

<style>
	.info-card {
		position: relative;
		transition:
			transform 0.3s ease,
			box-shadow 0.3s ease;
		animation: pulse-subtle 8s infinite alternate;
	}

	.info-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
	}

	.title-animated {
		position: relative;
		display: inline-block;
	}

	.title-animated::after {
		content: '';
		position: absolute;
		bottom: -4px;
		left: 50%;
		width: 0;
		height: 2px;
		background: #000;
		transition:
			width 0.4s ease,
			left 0.4s ease;
	}

	.title-animated:hover::after {
		width: 80%;
		left: 10%;
	}

	.info-item {
		transition:
			transform 0.2s ease,
			background-color 0.3s ease;
		padding: 8px;
		border-radius: 6px;
	}

	.info-item:hover {
		transform: scale(1.03);
		background-color: rgba(249, 250, 251, 0.8);
	}

	.emoji-bounce {
		display: inline-block;
		animation: bounce 2s infinite;
		animation-delay: calc(var(--animation-order, 0) * 0.5s);
	}

	p:nth-child(2) .emoji-bounce {
		--animation-order: 0;
	}
	p:nth-child(3) .emoji-bounce {
		--animation-order: 1;
	}
	p:nth-child(4) .emoji-bounce {
		--animation-order: 2;
	}
	p:nth-child(5) .emoji-bounce {
		--animation-order: 3;
	}

	@keyframes bounce {
		0%,
		20%,
		50%,
		80%,
		100% {
			transform: translateY(0);
		}
		40% {
			transform: translateY(-5px);
		}
		60% {
			transform: translateY(-3px);
		}
	}

	@keyframes pulse-subtle {
		0% {
			box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
		}
		100% {
			box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
		}
	}
</style>
