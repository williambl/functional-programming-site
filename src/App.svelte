<script>
	import { inview } from 'svelte-inview';

	const possibleElements = ["λ", "λλ", ">>==", "A monad is a monoid in the category of endofunctors.", "map", "filter", "reduce", "flatMap", "flatmap", "Int -> Int -> Int -> Int -> Int"]

	let elements = [];

	function createElement() {
		const idx = Math.round(Math.random() * (possibleElements.length-1));
		elements = [...elements, {text: possibleElements[idx], timing: 1.2+Math.random()*7}]
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
		<p class="code" style="animation-duration: {element.timing}s;">{element.text}</p>
	{/each}

	<div use:inview on:enter={createElements}></div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		overflow-x: hidden;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
	}

	.code {
		font-family: "Fira Code", "Courier New", monospace;
		position: relative;
		animation-delay: 1.25s;
		animation-name: zipAcross;
		animation-fill-mode: backwards;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	@keyframes zipAcross {
		from { right: 100vw }
		to { right: -100vw }
	}
</style>