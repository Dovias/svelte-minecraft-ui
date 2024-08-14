<script context="module" lang="ts">
	import type { ButtonProps } from "$lib/Button.svelte";
	import type { NavigationMenuColumns } from "./NavigationMenu.svelte";

	export type NavigationSectionProps = {
		items: NavigationSectionItemProps[]
	};

	export type NavigationSectionItemProps = {
		span?: Omit<NavigationMenuColumns, 1>
		column?: NavigationMenuColumns

		label?: ButtonProps['label']
		icons?: ButtonProps['icons']

	};
</script>

<script lang="ts">
    import Button from "$lib/Button.svelte";

	export let items: NavigationSectionProps['items'];

	function constructClassList(items: NavigationSectionItemProps[], index: number) {
		let classes = '';

		let {span, column} = items[index];
		if (span) {
			classes = `span-${span} `;
		}
		if (column) {
			classes += `column-${column} `;
		}
		return classes.trim();
	}

</script>


<div class="section">
		{#if Array.isArray(items)}
			{#each items as props, index}
				<div class={constructClassList(items, index)}>
					<Button fullSize label={props.label} icons={props.icons}  />
				</div>
			{/each}
		{/if}
</div>

<style>
	.section {
		display: grid;
		grid-template-columns: minmax(2.55em, auto) 1fr 1fr minmax(2.55em, auto);

		gap: 0.9em;
	}

	.column-1 {
		grid-column-start: 1;
	}

	.column-2 {
		grid-column-start: 2;
	}

	.column-3 {
		grid-column-start: 3;
	}

	.column-4 {
		grid-column-start: 4;
	}

	.span-2 {
		grid-column-end: span 2;
	}

	.span-3 {
		grid-column-end: span 3;
	}

	.span-4 {
		grid-column-end: span 4;
	}
</style>