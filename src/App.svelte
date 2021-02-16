<script>
	import MultiCarousel from './components/MultiCarousel.svelte';
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

	let carouselIndex = 0;

	const carouselImages = [
		[
			{path: "images/Flock_screenshot.png", alt: "flock1", id: "image1"},
			{path: "images/Flock_screenshot2.png", alt: "flock2", id: "image2"},
			{path: "images/Flock_screenshot3.png", alt: "flock3", id: "image3"},
			{path: "images/test-cm_curl.png", alt: "earth1", id: "image4"},
			{path: "images/test-cm_NEO_pollution_mort.png", alt: "earth2", id: "image5"},
			{path: "images/test-cm_New_Lacerta.png", alt: "earth3", id: "image6"}
		],

		[
			{path: "images/Flock_screenshot.png", alt: "flock1", id: "image1"},
			{path: "images/Flock_screenshot2.png", alt: "flock2", id: "image2"},
			{path: "images/Flock_screenshot3.png", alt: "flock3", id: "image3"},
			{path: "images/test-cm_curl.png", alt: "earth1", id: "image4"},
			{path: "images/test-cm_NEO_pollution_mort.png", alt: "earth2", id: "image5"},
			{path: "images/test-cm_New_Lacerta.png", alt: "earth3", id: "image6"}
		],

		[
			{path: "images/Flock_screenshot.png", alt: "flock1", id: "image1"},
			{path: "images/Flock_screenshot2.png", alt: "flock2", id: "image2"},
			{path: "images/Flock_screenshot3.png", alt: "flock3", id: "image3"},
			{path: "images/test-cm_curl.png", alt: "earth1", id: "image4"},
			{path: "images/test-cm_NEO_pollution_mort.png", alt: "earth2", id: "image5"},
			{path: "images/test-cm_New_Lacerta.png", alt: "earth3", id: "image6"}
		],

		[
			{path: "images/Flock_screenshot.png", alt: "flock1", id: "image1"},
			{path: "images/Flock_screenshot2.png", alt: "flock2", id: "image2"},
			{path: "images/Flock_screenshot3.png", alt: "flock3", id: "image3"},
			{path: "images/test-cm_curl.png", alt: "earth1", id: "image4"},
			{path: "images/test-cm_NEO_pollution_mort.png", alt: "earth2", id: "image5"},
			{path: "images/test-cm_New_Lacerta.png", alt: "earth3", id: "image6"}
		]
	]

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
	<div id="carousel-container">
		<MultiCarousel 
			{carouselImages}
		/>
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

	header {
		display: flex;
		justify-content: space-between;
	}

	h1 {
		font-size: 2em;
	}

	#carousel-container {
		width: 100%;
		height: 300px;
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		overflow-x: hidden;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>