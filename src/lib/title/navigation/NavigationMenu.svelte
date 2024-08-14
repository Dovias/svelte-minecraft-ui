<script context="module" lang="ts">
	import type { NavigationSectionProps } from './NavigationSection.svelte';

	export type NavigationMenuColumns = 1 | 2 | 3 | 4;

	export type NavigationMenuProps = {
		sections: NavigationSectionProps[]
	};
</script>

<script lang="ts">
	import NavigationSection from "./NavigationSection.svelte";

	export let sections: NavigationMenuProps['sections'];
</script>

<nav class="menu">
	{#if Array.isArray(sections)}
		{#each sections as props}
			<NavigationSection {...props} />
		{/each}
	{/if}
</nav>

<style>
	.menu {
		display: flex;
		flex-direction: column;

		gap: 2em;
	}
</style>