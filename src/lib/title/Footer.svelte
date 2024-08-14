<script lang="ts">
	export let branding: string;
	export let copyright: string;
</script>

<footer class="footer">
	<p class="footer-text">{branding}</p>
	<p class="footer-text hover-underline align-right">{copyright}</p>
</footer>

<style>
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