<script>
	import MultiCarousel from './components/MultiCarousel.svelte';
	import Grid from './Grid.svelte';
	import Card from './Card.svelte';

	// data //

	const projectDataUrl = "./projects.json";

	async function fetchJSONData(url) {
		let data = [];
		const res = await fetch(url);
		const jsonObj = await res.json();
		console.log(jsonObj)
		for(var item in jsonObj) {
			data.push(jsonObj[item]);
		}

		if (res.ok) {
			return data;
		} else {
			throw new Error(data);
		}
	}

	let id = 0;

	const carouselImages = [
		[
			{path: "images/Flock/MKG_Beauty_Ausstellungsansicht_1_full.jpg", alt: "earth3", caption: "Flock installation at MKG Hamburg", id: id++ },
			{path: "images/Flock/003_20181023_m.JPG", alt: "flock1", caption: "Flock installation at MAK Vienna", id: id++ },
			{path: "images/Flock/015_20181023_m.JPG", alt: "flock2", caption: "Beauty Show opening party", id: id++ },
			{path: "images/Flock/Beauty-3C4B-2019-23-768x432.jpg", alt: "flock3", caption: "Visitors to Flock at MAK Vienna", id: id++ },
			{path: "images/Flock/Hamburg_Foto_Henning_Rogge_5.jpg", alt: "earth1", caption: "Flock installation at MKG Hamburg", id: id++ },
			{path: "images/Flock/IMG_7802.jpg", alt: "earth2", caption: "Visitor with Flock at Beauty Show opening party", id: id++ }
		],

		[
			{path: "images/SeeingEarth/earth-visualisation.jpg", alt: "flock1", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-08-28-0130.png", alt: "flock1", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/1880.png", alt: "flock1", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-08-20-000000.png", alt: "flock2", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-09-02-000000.png", alt: "flock3", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-09-08-0730.png", alt: "earth1", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-10-11-163000.png", alt: "earth2", caption: "lovely picture", id: id++ },
			{path: "images/SeeingEarth/2019-10-13-001535.jpg", alt: "earth3", caption: "lovely picture", id: id++ }
		],

		[
			{path: "images/Rain+Terrain/ar-sandbox.jpg", alt: "flock1", caption: "lovely picture", id: id++ },
			{path: "images/Rain+Terrain/131547489_381821539545701_4592621555594319789_n.jpg", alt: "flock2", caption: "lovely picture", id: id++ },
			{path: "images/Rain+Terrain/IMG_0509.JPG", alt: "flock3", caption: "lovely picture", id: id++ },
			{path: "images/Rain+Terrain/IMG_0803.JPG", alt: "earth1", caption: "lovely picture", id: id++ },
			{path: "images/Rain+Terrain/IMG_0890.jpg", alt: "earth2", caption: "lovely picture", id: id++ },
			{path: "images/Rain+Terrain/IMG_7602 2.JPG", alt: "earth3", caption: "lovely picture", id: id++ }
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