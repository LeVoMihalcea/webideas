<script>
	import Card, { Actions, Content } from '@smui/card';
	import Chip, { Set, Text } from '@smui/chips';

	export let id;
	export let name;
	export let technologies = [];
	export let votes;
</script>

<Card>
	<Content>
		<p>{name}</p>
	</Content>

	<div class='votes mdc-theme--secondary-bg'>
		{votes}
	</div>

	<Actions>
		<Set chips={technologies.slice(0, 3)} let:chip nonInteractive>
			<Chip {chip}>
				<Text>{chip}</Text>
			</Chip>
		</Set>
	</Actions>
</Card>

<style>
    p {
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
    }

    .votes {
        position: absolute;
        top: 10px;
        right: 10px;
        color: gray; /*todo: find out how to get accent color from theme*/
    }
</style>
