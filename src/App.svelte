<script>
	import Grid from './Grid.svelte';
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
		Carosel
	</div>
	<div>
		<Grid>
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