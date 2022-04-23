<script>
	import HomeList from './list/homeList.svelte';
</script>

<div class='container'>
	<h3>Web Ideas</h3>
	<HomeList />
</div>

<style>
		.container{
				width: 80%;
				margin: 0 auto;
		}


    @media (max-width: 1500px) {
        .container {
            width: 100%;
        }
    }
</style>