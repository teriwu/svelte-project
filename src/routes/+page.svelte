<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	let show = false
	import { fade } from 'svelte/transition';
	let visible = true;
	import { Modal } from 'flowbite-svelte';
	let showModal = false;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<button on:click={() => {showModal = !showModal}}>Modal</button>

<Modal title="this is my modal" open={showModal}/>

<section>
	<div class="grid place-items-center w-[600px] h-[900px] rounded-xl bg-red-800 shadow-2xl">

		<h1>
			<span class="welcome">
				<picture>
					<source srcset={welcome} type="image/webp" />
					<img class="bg-white bg-opacity-5" src={welcome_fallback} alt="Welcome" />
				</picture>
			</span>
			
		</h1>
		<div class="bg-white bg-opacity-10 w-1/2 h-auto text-3xl font-bold text-center">
			to your new<br />SvelteKit app
		</div>
		
		<h2>
			try editing <strong>src/routes/+page.svelte</strong>
		</h2>
		
		<Counter />
		
		<button class="curse-zoom-in hover:bg-blue-200 bg-blue-500 rounded-sm py-2 px-1 text-white" on:click={() => {show = !show}}>Hi!</button>

		{#if show}	
		<img transition:fade src="https://cdn.discordapp.com/emojis/801435251397099570.webp?size=96&quality=lossless" alt="panda cartoon lying on side" />
		{/if}
		
	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
