<script>
	import Grid from './Grid.svelte';
	import Card from './Card.svelte';

	const projectDataUrl = "./projects.json";

	async function fetchJSONData(url) {
		let data = [];
		const res = await fetch(url);
		const jsonObj = await res.json();
		console.log(jsonObj)
		for(var item in jsonObj) {
			data.push(jsonObj[item]);
		}

		console.log(data);

		if (res.ok) {
			return data;
		} else {
			throw new Error(data);
		}
	}
</script>

<main>
	<header>
		<h1>Logo</h1>
		<div>
			<ul>
				<li>Work</li>
				<li>Contact</li>
			</ul>
		</div>
	</header>
	<div>
		Carousel
	</div>
	<div>
		<Grid>
			{#await fetchJSONData(projectDataUrl)}
				<p>loading</p>
			{:then projects}
				{#each projects as project}
					<Card {project} />
				{/each}
			{:catch error}
				{(console.log(error.message))}
			{/await}
		</Grid>
	</div>
	<footer>
		Colophon & Copyright
	</footer>
</main>

<style lang="scss">
	main {
		text-align: left;
		color: black;
		padding: 1em;
		max-width: 1050px;
		margin: 0 auto;
		border: 1px solid black;
	}

	h1 {
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>