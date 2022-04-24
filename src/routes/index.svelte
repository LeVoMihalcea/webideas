<script>
	import HomeList from './list/homeList.svelte';
	import Navbar from './shared/_navbar.svelte'

</script>

<Navbar/>

<div class='container'>
	<HomeList />
</div>

<style>
    .container {
        width: 80%;
        margin: 0 auto;
    }


    @media (max-width: 1500px) {
        .container {
            width: 95%;
        }
    }
</style>