<script>
	import { onMount } from 'svelte';

	import LayoutGrid, { Cell } from '@smui/layout-grid';

	import { webIdeas } from '../../stores/store.js';

	import Project from './_project.svelte';
	import SearchArea from './_searchArea.svelte';
	import Spinner from '../shared/_spinner.svelte';

	let searchKey = '';

	function filterAndSortIdeas(ideas) {
		return ideas
			.filter(idea => idea.name.includes(searchKey))
			.sort((a, b) => b.votes - a.votes);
	}

	async function fetchIdeas() {
		fetch('https://a8ce727f-0a6e-4f3d-bfe2-5021002c9701.mock.pstmn.io/ideas')
			.then(response => response.json())
			.then(ideas => webIdeas.set(filterAndSortIdeas(ideas)))
			.catch(() => {
				return [];
			});
	}

	onMount(() => fetchIdeas());
</script>

<SearchArea bind:searchKey on:input={fetchIdeas} />

{#if $webIdeas === null}
	<div class='spinner'>
		<Spinner />
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
</style>


