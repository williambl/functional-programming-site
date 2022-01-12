<script>
	import { inview } from 'svelte-inview';

	const possibleElements = ["λ", "λλ", ">>==", "A monad is a monoid in the category of endofunctors.", "map", "filter", "reduce", "flatMap", "flatmap", "Int -> Int -> Int -> Int -> Int"]

	let elements = [];

	function createElement() {
		const idx = Math.round(Math.random() * (possibleElements.length-1));
		elements = [...elements, possibleElements[idx]]
	}

	function createElements() {
		for (let i = 0; i < 50; i++) {
			createElement()
		}
	}

	createElements()
</script>

<main>
	<h1>Functional Programming</h1>
	{#each elements as element}
		<p class="code">{element}</p>
	{/each}

	<div use:inview on:enter={createElements}></div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
	}

	.code {
		font-family: "Fira Code", "Courier New", monospace;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>