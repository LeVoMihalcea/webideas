<script>
	import HomeList from './list/homeList.svelte';

	import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
</script>

<!--https://www.npmjs.com/package/@smui/top-app-bar-->
<TopAppBar
	variant='static'
>
	<Row>
		<Section>
			<Title>Web Ideas</Title>
		</Section>
	</Row>
</TopAppBar>

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