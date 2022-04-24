<script>
	import Textfield from '@smui/textfield';

	import {createEventDispatcher} from 'svelte';

	const dispatch = createEventDispatcher();

	export let searchKey;

	function handleValueChanged() {
		dispatch('input', searchKey);
	}
</script>

<div class='search-bar'>
	<Textfield
		updateInvalid
		bind:value={searchKey}
		on:input={handleValueChanged}
		style='width: 100%'
		label='Search your next awesome project!'
	/>
</div>