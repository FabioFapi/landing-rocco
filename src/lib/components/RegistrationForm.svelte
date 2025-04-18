<!-- src/lib/components/RegistrationForm.svelte -->
<script>
	import { fly, fade } from 'svelte/transition';
	import { spring } from 'svelte/motion';

	let submitted = false;
	let focused = null;

	function handleFocus(field) {
		focused = field;
	}

	function handleBlur() {
		focused = null;
	}

	function handleSubmit(e) {
		// Keep the original form submission behavior
		// Just add a visual feedback for the demo
		submitted = true;
		// The form will still submit as normal
	}
</script>

<section class="flex w-full justify-center px-6 py-12">
	<form
		action="https://formsubmit.co/secretary@womblab.com"
		method="POST"
		class="w-full max-w-[360px] space-y-6 text-center"
		on:submit={handleSubmit}
		in:fade={{ duration: 800, delay: 300 }}
	>
		<!-- Disattiva captcha di default (opzionale) -->
		<input type="hidden" name="_captcha" value="false" />

		<!-- Titolo -->
		<h2 class="text-lg leading-snug font-semibold" in:fly={{ y: -20, duration: 700, delay: 500 }}>
			Please kindly RSVP by XXX<br />
			using the form below.
		</h2>

		<!-- First Name -->
		<div in:fly={{ y: 20, duration: 700, delay: 700 }}>
			<input
				type="text"
				name="First Name"
				placeholder="First Name"
				class="w-full rounded-full border border-black px-4 py-3 text-center text-base transition-all duration-300"
				class:shadow-md={focused === 'firstName'}
				required
				on:focus={() => handleFocus('firstName')}
				on:blur={handleBlur}
			/>
		</div>

		<!-- Last Name -->
		<div in:fly={{ y: 20, duration: 700, delay: 900 }}>
			<input
				type="text"
				name="Last Name"
				placeholder="Last Name"
				class="w-full rounded-full border border-black px-4 py-3 text-center text-base transition-all duration-300"
				class:shadow-md={focused === 'lastName'}
				required
				on:focus={() => handleFocus('lastName')}
				on:blur={handleBlur}
			/>
		</div>

		<!-- Submit Button -->
		<div in:fly={{ y: 20, duration: 700, delay: 1100 }}>
			<button
				type="submit"
				class="w-full transform rounded-full bg-black py-3 text-center text-base font-semibold transition-transform duration-300 hover:scale-105"
			>
				<span class="bg-gradient-to-r from-[#d8b878] to-[#e4c88f] bg-clip-text text-transparent">
					Count me
				</span>
			</button>
		</div>

		{#if submitted}
			<div in:fly={{ y: -10, duration: 500 }} class="font-medium text-green-600">
				Thank you for your response!
			</div>
		{/if}
	</form>
</section>
