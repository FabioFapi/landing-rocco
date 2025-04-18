<!-- src/lib/components/RegistrationForm.svelte -->

<section class="flex w-full justify-center px-6 py-12">
	<form
		action="https://formsubmit.co/segretary@womblab.com" 
		method="POST"
		class="w-full max-w-[360px] space-y-6 text-center"
	>
		<!-- Disattiva captcha di default (opzionale) -->
		<input type="hidden" name="_captcha" value="false" />

		<!-- Titolo -->
		<h2 class="text-lg font-semibold leading-snug">
			Please kindly RSVP by XXX<br />
			using the form below.
		</h2>

		<!-- First Name -->
		<input
			type="text"
			name="First Name"
			placeholder="First Name"
			class="w-full px-4 py-3 border border-black rounded-full text-center text-base"
			required
		/>

		<!-- Last Name -->
		<input
			type="text"
			name="Last Name"
			placeholder="Last Name"
			class="w-full px-4 py-3 border border-black rounded-full text-center text-base"
			required
		/>

		<!-- Submit Button -->
		<button
			type="submit"
			class="w-full py-3 bg-black text-base font-semibold text-center rounded-full"
		>
			<span class="bg-gradient-to-r from-[#d8b878] to-[#e4c88f] bg-clip-text text-transparent">
				Count me
			</span>
		</button>
	</form>
</section>
