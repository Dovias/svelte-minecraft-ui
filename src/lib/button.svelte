<script lang="ts" context="module">
	import { browser } from '$app/environment';



	let clickSound: HTMLAudioElement;

	if (browser) {
		clickSound = new Audio('button/click.ogg')
	}

	function playSound() {
		clickSound.play();
	}
</script>

<script>
	export let fullWidth = false;
	export let compact = false;
</script>

<button on:mousedown={playSound} class:full-width={fullWidth} class:compact={compact}><slot /></button>


<style>
	button {
		position: relative;

		font-family: inherit;
		font-size: inherit;
		color: inherit;
		text-shadow: 0.1em 0.15em 0 rgba(0, 0, 0, 0.53);
		background: url('button/texture.png') left / 20em;
		border: 0;
		box-shadow: inset 0.14em 0.14em 0 #AFAFAF;
		image-rendering: pixelated;

		padding: var(--button-padding, 0.25em 1em 0.55em 1em);
		margin: var(--button-margin, 0.36em);

		outline: 0.15em solid black;
	}

	button:hover, button:focus {
		outline-color: white;
	}

	button::after {
		position: absolute;
		top: 0;
		left: 0;
		box-shadow: inset -0.14em -0.25em 0 rgba(0, 0, 0, 0.3);


		content: '';

		display: block;
		
		width: 100%;
		height: 100%;
	}

	.full-width {
    	width: 100%;
    }
	
	.compact {
		padding: var(--button-compact-padding, 0.25em);
	}
</style>
