<script lang="ts">
	import { fade } from 'svelte/transition';

	export let progress: number = 0;
	export let monochrome: boolean = false
</script>

<div class="overlay" class:monochrome transition:fade={{ delay: 500, duration: 1000 }}>
	<div class="content">
		<img src="branding/studio.png" alt="Studio branding" class="branding">
		<progress value={progress} max="100" class="progress-bar" transition:fade={{ duration: 1000 }}></progress>
	</div>
</div>

<style>
	.overlay {
			position: absolute;
			top: 0;
			left: 0;

			width: 100%;
			height: 100%;

			display: flex;
			flex-direction: column;
			justify-content: center;

			background: #EF323D;
	}

	.monochrome {
			background: #000;
	}

	.content {
		margin: auto;
		padding-top: 8%;

	  max-width: 60%;
	  max-height: 60%;
	}

	.branding {
		display: block;

	  width: 84em;

	  max-width: 100%;
	  max-height: 100%;

		image-rendering: crisp-edges;

		margin: auto;
	}

	.progress-bar {
	  display: block;

		width: 100%;
	  height: 1.5em;

	  margin-top: 20%;

	  background: none;

		border: 0.225em solid transparent;
		outline: 0.225em solid #fff;
  }

  .progress-bar::-webkit-progress-bar {
	  background: none;
  }

  .progress-bar::-webkit-progress-value {
	  transition: 1s width;

	  background: #fff;
  }
  .progress-bar::-moz-progress-bar {
	  transition: 1s width;

	  background: #fff;
	}


</style>