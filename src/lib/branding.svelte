<div class="branding-container">
	<img src="branding.png" class="branding" alt="branding" />
	<p class="splash">It came from space.</p>
</div>


<style>
	.branding-container {
		position: relative;
	}

	.branding {
		width: 100%;
		margin-bottom: 3em;
	}

	@keyframes splash {
		0% {
			transform: rotate(-20deg) perspective(1em) translateZ(0em);

		}
		33% {
			transform: rotate(-20deg) perspective(1em) translateZ(0.05em);
		}
		100% {
			transform: rotate(-20deg) perspective(1em);

		}
	}

	.splash {
		position: absolute;
		bottom: 35%;
		right: -21%;
		
		transform-style: preserve-3d;

		font-size: 1.25em;
		font-family: inherit;
		color: #FFFF00;
		text-shadow: 0.12em 0.12em 0 #3F3F00;

		animation: 0.5s cubic-bezier(0, 0, 0.6, 1) infinite splash;
	}
</style>