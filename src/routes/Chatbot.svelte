<script lang="ts">
	import Contact from './Contact.svelte';

    import Send from '$lib/Images/send.svg';

	let currentQuestion = 0;

	// @ts-ignore
	let form;
	// @ts-ignore
	async function handleSubmit(event) {
		event.preventDefault();
		// @ts-ignore
		const data = new FormData(form);

		await fetch('/', {
			method: 'POST',
			headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
			// @ts-ignore
			body: new URLSearchParams(Array.from(data)).toString()
		})
			.then(() => (location.href = '/kiitos'))
			.catch((error) => alert(error));
	}

function handleNext() {
    // Increment currentQuestion if the current question is valid
    if (form[currentQuestion].value !== '' || !form[currentQuestion].required) {
        currentQuestion = currentQuestion + 1;
    }
}

	const questions = [
		{ label: 'Mikä on nimesi?', type: 'text', name: 'Nimi', placeholder: 'Nimi', required: true },
		{
			label: 'Mikä on puhelinnumerosi?',
			type: 'tel',
			name: 'puhelin',
			placeholder: 'Puhelinnumero',
			required: true
		},
		{
			label: 'Mikä on sähköpostiosoitteesi',
			type: 'email',
			name: 'email',
			placeholder: 'Sähköpostiosoite',
			required: true
		},
		{
			label: 'Mihin osoitteeseen haluat laskun?',
			type: 'text',
			name: 'Laskutusosoite',
			placeholder: 'Laskutusosoite',
			required: true
		},
		{
			label: 'Mistä osoitteesta muutetaan?',
			type: 'text',
			name: 'Osoite, josta muutetaan',
			placeholder: 'lähtö osoite',
			required: true
		},
		{
			label: 'Missä kerroksessa lähtökohde on?',
			type: 'number',
			name: 'lähtö-kerros',
			placeholder: 'lähtö kerros',
			required: true
		},
		{
			label: 'Onko lähtökohteessa hissiä?',
			type: 'radio',
			name: 'hissi lähtökohteessa',
			options: [
				{ label: 'Kyllä', value: 'Kyllä' },
				{ label: 'Ei', value: 'Ei' }
			],
			required: true
		},
		{
			label: 'Mihin osoitteeseen muutetaan?',
			type: 'text',
			name: 'Osoite, johon muutetaan',
			placeholder: 'saapumis osoite',
			required: true
		},
		{
			label: 'Missä kerroksessa uusi kohde on?',
			type: 'number',
			name: 'saapumis-kerros',
			placeholder: 'saapumis kerros',
			required: true
		},
		{
			label: 'Onko uudessa kohteessa hissiä?',
			type: 'radio',
			name: 'hissi uudessa kohteessa',
			options: [
				{ label: 'Kyllä', value: 'Kyllä' },
				{ label: 'Ei', value: 'Ei' }
			],
			required: true
		},
		{
			label: 'Mikä on muutettavan asunnon neliöt (m²)?',
			type: 'number',
			name: 'Muutettavan asunnon neliöt',
			placeholder: 'Muutettavan asunnon neliöt',
			min: -1,
			required: true
		},
		{
			label: 'Paljonko on muuttokohteiden välinen etäisyys (km)?',
			type: 'number',
			name: 'Muuttokohteiden välinen etäisyys',
			placeholder: 'Muuttokohteiden välinen etäisyys',
			min: -1,
			required: true
		},
		{
			label: 'Onko erityisen painavavia huonekaluja (yli 100kg), kuten pianoa yms.',
			type: 'textarea',
			name: 'Erityisen painavat huonekalut (yli 100kg), kuten pianot yms.',
			placeholder: 'Erityisen painavat huonekalut (yli 100kg), kuten pianot yms.',
			required: true
		},
		{ label: 'Minä päivänä haluat muuton?', type: 'date', name: 'muuttopäivä', required: false },
		{
			label: 'Mistä löysit meidät?',
			type: 'textarea',
			name: 'Mistä löysit meidät?',
			placeholder: 'Mistä löysit meidät?',
			required: false
		},
		{
			label: 'Onko muuta huomioitavaa?',
			type: 'textarea',
			name: 'Muuta huomioitavaa',
			placeholder: 'Muuta huomioitavaa',
			required: false
		}
	];
</script>

<form
	id="lomake"
	class="content"
	bind:this={form}
	name="contact"
	data-netlify="true"
	on:submit={handleSubmit}
>
	<br />
	<h2>
		<strong>Chatti Botti</strong>
	</h2>
	<small> Tilaa tarjouspyyntö chatin kautta! </small>

	{#each questions as { label, type, name, placeholder, required, min, options }, i}
		<!-- if not currentQuestion style="display: none" -->
		<div class={i === currentQuestion ? 'form-question' : ''} style="display: {i <= currentQuestion ? 'block' : 'none'}">
			<label for={name}>{label}</label>
			{#if type === 'radio'}
				{#each options as { label, value }, i}
					<input {type} id={name + i} {name} {value} {required} />
					<label for={name + i}>{label}</label>
				{/each}
			{:else}
				<input {type} id={name} {name} {placeholder} {required} {min} />
			{/if}
            <button on:click={handleNext} style="display: {i === currentQuestion ? 'block' : 'none'}"> 
                <img src={Send} alt="Lähetä">
            </button>
		</div>
	{/each}
</form>
