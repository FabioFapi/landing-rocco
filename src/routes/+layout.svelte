<script>
	import '../app.css';

	let { children } = $props();
</script>
<svelte:head>
	<title>Rocco's Party</title>
	<meta
		name="description"
		content="Dear Friends and Family,
I am delighted to invite you to join me in celebrating a special milestone — my birthday.

It would mean a lot to have you there as I mark another year of life, growth, and gratitude.

Your presence would truly make the day memorable, and I would be honored to celebrate this occasion with those closest to me.

I truly look forward to celebrating together and sharing this joyful day with you.

Warm regards, Rocco"
	/>
	<meta name="robots" content="max-image-preview:large" />
	<meta http-equiv="Content-Language" content="it-IT" />
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<meta
		name="keywords"
		content="PROMOZIONE, PROGETTAZIONE, ORGANIZZAZIONE ED EROGAZIONE DI ATTIVITÀ FORMATIVA ATTRAVERSO EVENTI, CONGRESSI E E CORSI FORMATIVI IN GENERALE ANCHE IN FORMA FAD,FORMAZIONE IN MEDICINA"
	/>
	<meta property="og:title" content="Rocco's Party" />
	<meta
		property="og:description"
		content="Dear Friends and Family,
I am delighted to invite you to join me in celebrating a special milestone — my birthday.

It would mean a lot to have you there as I mark another year of life, growth, and gratitude.

Your presence would truly make the day memorable, and I would be honored to celebrate this occasion with those closest to me.

I truly look forward to celebrating together and sharing this joyful day with you.

Warm regards, Rocco"
	/>
	<meta property="og:url" content="https://rocco-s-party.vercel.app/" />
	<meta property="og:type" content="website" />
	<meta property="og:site_name" name="og:site_name" content="Rocco's Party" />
	<meta property="og:locale" name="og:locale" content="it-IT" />
	<meta property="og:image" content="https://rocco-s-party.vercel.app/images/hero.jpg" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="Rocco's Party" />
	<meta name="twitter:image" content="https://rocco-s-party.vercel.app/images/hero.jpg" />
	<meta
		name="twitter:description"
		content="Dear Friends and Family,
I am delighted to invite you to join me in celebrating a special milestone — my birthday.

It would mean a lot to have you there as I mark another year of life, growth, and gratitude.

Your presence would truly make the day memorable, and I would be honored to celebrate this occasion with those closest to me.

I truly look forward to celebrating together and sharing this joyful day with you.

Warm regards, Rocco"
	/>
</svelte:head>


{@render children()}
