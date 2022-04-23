<script>
	import { onMount } from 'svelte';

	import CircularProgress from '@smui/circular-progress';
	import LayoutGrid, { Cell } from '@smui/layout-grid';

	import { webIdeas } from '../../stores/store.js';

	import Project from './_Project.svelte';

	onMount(async () => {
		fetch('https://a8ce727f-0a6e-4f3d-bfe2-5021002c9701.mock.pstmn.io/ideas')
			.then(response => response.json())
			.then(ideas => {
				webIdeas.set(ideas);
			})
			.catch(() => {
				return [];
			});
	});
</script>


{#if $webIdeas.length === 0}
	<CircularProgress style='height: 100px; width: 100px' indeterminate />
{/if}

<LayoutGrid>
	{#each $webIdeas.slice(0, 20) as idea}
		<Cell>
			<Project {...idea}/>
		</Cell>
	{/each}
</LayoutGrid>

<style>

</style>


