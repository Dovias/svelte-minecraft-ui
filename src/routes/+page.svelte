<script lang="ts">
	import Header from "$lib/title/Header.svelte";
	import Panorama from "$lib/Panorama.svelte";
	import NavigationMenu from "$lib/title/navigation/NavigationMenu.svelte";
	import Footer from "$lib/title/Footer.svelte";
  import { fade } from 'svelte/transition';
  import { onMount } from "svelte";
  import LoadingOverlay from "$lib/load/LoadingOverlay.svelte";



  let branding = "Minecraft 1.21.1";

  // evil fake loading for simulation of real game loading
  let progress = 5;
  let loaded = false;
  onMount(() => {
      setTimeout(() => {
          progress += Math.floor(Math.random() * 80);

					setTimeout(() => {
						progress = 100;

						setTimeout(() => loaded = true, 1000 + Math.floor(Math.random() * 500));
          }, 900 + Math.floor(Math.random() * 2000));
      }, 2000 + Math.floor(Math.random() * 2000));
  });
</script>

<svelte:head>
	<title>{branding}</title>
</svelte:head>

<Panorama />
{#if loaded}
	<div class="title-screen" transition:fade={{ duration: 1250, delay: 1500 }}>
		<div class="content">
			<Header splashText="12 herbs and spices!" />

			<NavigationMenu sections={[
				{
					items: [
						{
							column: 2,
							span: 2,
							label: 'Singleplayer'
						},
						{
							column: 2,
							span: 2,
							label: 'Multiplayer'
						},
						{
							column: 2,
							span: 2,
							label: 'Minecraft Realms',
							icons: [
								{ path: 'button/icons/realms/trial-available.gif', label: 'trial available', size: 'font'	},
								{ path: 'button/icons/realms/news.png', label: 'news', size: 'full'	},
							]
						},
					],
				},
				{
					items: [
						{ icons: [{ path: "button/icons/language.png", label: "language", size: 'full' }]},
						{ label: 'Options...' },
						{ label: 'Quit game' },
						{ icons: [{ path: "button/icons/accessibility.png", label: "accessibility", size: 'full' }]}
					]
				}
			]} />
		</div>
		<Footer branding={branding} copyright="Copyright Mojang AB. Do not distribute!" />
	</div>
{:else}
	<LoadingOverlay {progress} />
{/if}

<style>
	.title-screen {
		position: absolute;
		top: 0;
		left: 0;

		font-size: 1.3em;

		display: flex;
		flex-direction: column;
		justify-content: space-between;

		height: 100%;
		width: 100%;

		overflow: hidden;
	}

	.content {
		display: flex;
		flex-direction: column;

		justify-content: space-between;

		max-width: 32.9175em;
		height: 28.25em;
		margin: 4.33em auto;
	}
</style>