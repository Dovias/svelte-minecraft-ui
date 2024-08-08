<script>
	import Branding from "$lib/branding.svelte";
    import Button from "$lib/button.svelte";
    import Panorama from "$lib/panorama.svelte";
</script>
<Panorama />
<div class="title-screen">
	<div class="menu">
		<Branding />

		<nav class="navigation-buttons">
			<div class="primary-navigation-container">
				<Button fullWidth>Singleplayer</Button>
				<Button fullWidth>Multiplayer</Button>
				<Button fullWidth>Minecraft Realms <span class="realms-icons">
					<img src="button/icons/realms/trial-available.gif" class="realms-trial-available" alt="realms trial available" />
					<img src="button/icons/realms/news.png" class="realms-news" alt="realms news available" />
				</span></Button>
			</div>
			<div class="secondary-navigation-container">
				<Button compact><img src="button/icons/language.png" class="icon" alt="language" /></Button>	
			</div>
			<div class="secondary-navigation-container">
				<Button fullWidth>Options...</Button>
			</div>
			<div class="secondary-navigation-container">
				<Button fullWidth>Quit game</Button>
			</div>
			<div class="secondary-navigation-container">
				<Button compact><img src="button/icons/accessibility.png" class="icon" alt="language" /></Button>	
			</div>
		</nav>
	</div>
	<footer class="footer">
		<p class="footer-text">Minecraft 1.21</p>
		<p class="footer-text hover-underline align-right">Copyright Mojang AB. Do not distribute!</p>
	</footer>
</div>

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

	.menu {
		max-width: 32.9175em;
		margin: auto;
	}

	.navigation-buttons {
		display: grid;
		grid-template-columns: auto 1fr 1fr auto;
		gap: 0.6em;


		--button-margin: 0.33em 0
	}

	.primary-navigation-container {
		grid-column: 2 / span 2;
	}

	.secondary-navigation-container {
		grid-row: last-line;

		--button-compact-padding: 0.2em 0.2em 0	0.2em
	}
	
	.icon {
		height: 1.8em;
		width: 1.8em;
	}

	.realms-icons {
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;

		display: flex;
		align-items: center;
	}

	.realms-trial-available {
		display: block;

		width: 1em;
		height: 1em;
		margin: 0 0.25em 0 0.5em;
	}

	.realms-news {
		display: block;

		width: 1.75em;
		height: 1.85em;
		margin: -1px 0.25em 0 0.25em;

	}

	.text-icon-button-container {
		display: flex;

		--button-compact-padding: 0.25em 0.2em 0 0.25em
	}

	.footer {
		display: flex;
		justify-content: space-between;

		width: 100%;
		margin-top: 2em;
	}

	.footer-text {
		margin: 0.2em 0.4em;
		text-shadow: 0.12em 0.12em 0 #3F3F3F;
	}

	.hover-underline:hover {
		border-bottom: 2px solid;
	}

	.align-right {
		text-align: right;
	}
</style>