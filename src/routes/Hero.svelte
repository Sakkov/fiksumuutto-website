<script lang="ts">
	import Navbar from './Navbar.svelte';
	import { page } from '$app/stores';

	import Logo from '$lib/Images/Fiksukuljetuslogo1_0_kuusikulmiotaustalla.svg';
	import Logo_vaasa from '$lib/Images/Fiksukuljetuslogo1_21_vaasa_kuusikulmiotaustalla.svg';
</script>

<div class="logo">
	{#if $page.url.pathname.includes('pohjanmaa')}
		<img src={Logo_vaasa} alt="Fiksukuljetus Oy muutto Pohjanmaa" width="500" height="500" />
	{:else}
		<img src={Logo} alt="Fiksukuljetus Oy muutto pirkanmaa" width="500" height="500" />
	{/if}
</div>

<Navbar />
