<script>
	let firstName = '';
	let lastName = '';

	function submitForm() {
		alert(`RSVP sent for: ${firstName} ${lastName}`);
	}
</script>

<section class="flex w-full justify-center px-6 py-12">
	<form class="w-full max-w-[360px] space-y-6 text-center" on:submit|preventDefault={submitForm}>
		<h2 class="text-lg leading-snug font-semibold">
			Please kindly RSVP by XXX<br />
			using the form below.
		</h2>

		<input
			type="text"
			bind:value={firstName}
			placeholder="First Name"
			class="w-full rounded-full border border-black px-4 py-3 text-center text-base"
			required
		/>

		<input
			type="text"
			bind:value={lastName}
			placeholder="Last Name"
			class="w-full rounded-full border border-black px-4 py-3 text-center text-base"
			required
		/>

		<button
			type="submit"
			class="w-full rounded-full bg-black py-3 text-center text-base font-semibold"
		>
			<span class="bg-gradient-to-r from-[#d8b878] to-[#e4c88f] bg-clip-text text-transparent">
				Count me
			</span>
		</button>
	</form>
</section>
