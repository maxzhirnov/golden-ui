<script>
    import Feed from "./components/Feed.svelte";
</script>

<main>
	<h1>Golden feed:</h1>
	<Feed/>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>