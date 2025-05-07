<!-- src/lib/components/RegistrationForm.svelte -->

<section class="flex w-full justify-center px-6 py-12"
style="font-family: 'Garamond', serif;">
	<form
		action="https://formsubmit.co/secretary@womblab.com" 
		method="POST"
		class="w-full max-w-[360px] space-y-6 text-center"
	>
		<!-- Disattiva captcha di default (opzionale) -->
		<input type="hidden" name="_captcha" value="false" />

		<!-- Titolo -->
		<h2 class="text-lg font-serif font-bold text-black leading-snug">
			Allergies or dietary requirements
		</h2>

		<p class="text-base leading-relaxed">
			To make sure everyone has the best experience possible, please let me know if you have any allergies or dietary restrictions.
		</p>
		<!-- Full Name -->
		<input
			type="text"
			name="Full Name"
			placeholder="Full Name"
			class="w-full px-4 py-3 border border-black rounded-full text-center text-base"
			required
		/>

		<!-- Email -->
		<input
			type="text"
			name="Email"
			placeholder="Email"
			class="w-full px-4 py-3 border border-black rounded-full text-center text-base"
			required
		/>

		<input
			type="text"
			name="Allergies"
			placeholder="Allergies/ Dietary Restrictions"
			class="w-full px-4 py-3 border border-black rounded-full text-center text-base"
			required
		/>

		<!-- Submit Button -->
		<button
			type="submit"
			class="w-full py-3 bg-black text-base font-semibold text-center rounded-full"
		>
			<span class="bg-gradient-to-r from-[#d8b878] to-[#e4c88f] bg-clip-text text-transparent">
				Submit
			</span>
		</button>
	</form>
</section>
