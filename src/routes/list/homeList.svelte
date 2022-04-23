<script>
	import { onMount } from 'svelte';

	import CircularProgress from '@smui/circular-progress';
	import LayoutGrid, { Cell } from '@smui/layout-grid';
	import Textfield from '@smui/textfield';

	import { webIdeas } from '../../stores/store.js';

	import Project from './_Project.svelte';

	let searchKey = '';

	async function fetchIdeas() {
		fetch('https://a8ce727f-0a6e-4f3d-bfe2-5021002c9701.mock.pstmn.io/ideas')
			.then(response => response.json())
			.then(ideas => {
				ideas;
				webIdeas.set(ideas
					.filter(idea => idea.name.includes(searchKey))
					.sort((a, b) => b.votes - a.votes)
				);
			})
			.catch(() => {
				return [];
			});
	}

	onMount(() => fetchIdeas());
</script>


<div class='search-bar'>
	<Textfield
		updateInvalid
		bind:value={searchKey}
		on:input={fetchIdeas}
		style='width: 100%'
		label='Search your next awesome project!'
	/>
</div>


{#if $webIdeas === null}
	<div class='spinner'>
		<CircularProgress style='height: 200px; width: 200px' indeterminate />
	</div>
	{:else}
	<LayoutGrid>
		{#each $webIdeas?.slice(0, 21) as idea}
			<Cell>
				<Project {...idea} />
			</Cell>
		{/each}
	</LayoutGrid>
{/if}
<style>
    .spinner {
        margin: 20px auto;
        max-width: 200px;
    }

    .search-bar {
        width: 100%;
        margin: 20px auto;
    }
</style>


