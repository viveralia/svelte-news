<script>
	import { onMount } from 'svelte'
	import Article from './components/Article.svelte'
	import { newsApiKey } from './secrets.js'

	// Two empty objects to start with for the skeleton effect
	let articles = [{}, {}]

	onMount(async () => {
		const url = `https://newsapi.org/v2/top-headlines?country=us&apiKey=${newsApiKey}`
		const res = await fetch(url)
		const json = await res.json()
		articles = json.articles
	})
</script>

<div class="container px-4 md:px-8 lg:px-12 py-8">
	<h1 class="text-3xl font-bold mb-6">Svelte News</h1>
	<main class="grid grid-cols-1 lg:grid-cols-2 gap-6 lg:gap-12">
		{#each articles as article}
			<Article {...article} />
		{/each}
	</main>
</div>