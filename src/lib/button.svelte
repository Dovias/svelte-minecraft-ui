<script lang="ts" context="module">
	import { browser } from '$app/environment';

	export type IconSize = 'initial' | 'font' | 'full';

	export type Icon = {
		path: string
		label: string
		size?: IconSize
	};

	export type ButtonProps = {
		fullSize: boolean
		label?: string 
		icons?: Icon[];
	}

	let clickSound: HTMLAudioElement;

	if (browser) {
		clickSound = new Audio('button/click.ogg')
	}

	function playSound() {
		clickSound.play();
	}
</script>

<script lang="ts">
	export let fullSize: ButtonProps['fullSize'] = false;

	export let label: ButtonProps['label'];
	export let icons: ButtonProps['icons'];
</script>

<button on:mousedown={playSound} class="button" class:full-size={fullSize}>
	{#if label}
		<span class="label">{label}</span>
	{/if}

	<div class:icons={!label} class:label-icons={label}>
		{#if Array.isArray(icons) && icons.length > 0}
			{#each icons as icon}
				<img src={icon.path} alt={icon.label} class="icon" class:full-height={icon.size === 'full'} class:font-height={icon.size === 'font'} />
			{/each}
		{/if}
	</div>
</button>


<style>
	.button {
		position: relative;

		padding: var(--button-padding, 0.29em 0.1em 0.1em 0.25em);

		background: url('button/texture.png') left / 20em;
		box-shadow: inset 0.14em 0.14em 0 #AFAFAF;

		image-rendering: pixelated;

		font-family: inherit;
		font-size: 1.1em;
		color: inherit;
		text-shadow: 0.1em 0.15em 0 rgba(0, 0, 0, 0.53);

		border: 0;
		outline: 0.14em solid black;
	}

	.button:hover, .button:focus {
		outline-color: white;
	}

	.button::after {
	  content: '';

	  position: absolute;
		top: 0;
		left: 0;

	  display: block;
	  width: 100%;
	  height: 100%;

	  box-shadow: inset -0.14em -0.25em 0 rgba(0, 0, 0, 0.3);
	}

	.label {
		display: inline-block;
		margin-bottom: 0.4em;
	}

	.icons {
		height: 100%;
	}

  .label-icons {
	  position: absolute;
	  height: 79%;

	  top: 0;
	  right: 0;

	  margin: 0.22em 0.25em;
  }

	.icon {
		display: inline-block;
		vertical-align: middle;

	  margin-right: 0.5em;
  }

	.icon:last-child {
			margin: 0;
	}

	.font-height {
		height: 1em;
	}

	.full-height, .full-size {
	  height: 100%;
  }

	.full-size {
	  width: 100%;
	}
</style>
