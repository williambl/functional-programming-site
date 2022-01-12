<script>
	import { inview } from 'svelte-inview';

	const possibleElements = [
		"λ",
		"μ",
		">>==",
		"A monad is a monoid in the category of endofunctors.",
		"map",
		"map",
		"map",
		"map",
		"filter",
		"filter",
		"filter",
		"filter",
		"reduce",
		"filter",
		"filter",
		"flatmap",
		"flatmap",
		"flatmap",
		"flatmap",
		"functors",
		"functors",
		"profunctors",
		"profunctors",
		"Category Theory",
		"category theory",
		"Natural Transformations",
		"Int -> Int -> Int -> Int -> Int -> Int -> Int -> Int -> Int",
		"() -> a -> b -> (c, d, e) -> f -> a(b)(c)[d](e, f)",
		"(+ 1 1)",
		"upgrades.flatMapIndexed { idx, entry -> entry.map { Pair(it.key.position.add(-2.0*idx, 0.0, 0.0), Pair(it.value, it.value.data)) } }",
		"public <A, B, C, D> FunctionType<App2<Grate.Mu<A2, B2>, A, B>, App2<Grate.Mu<A2, B2>, C, D>> dimap(final Function<C, A> g, final Function<B, D> h)",
		"interface Mu extends Profunctor.Mu {}",
		"default Function15<T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, T11, T12, T13, T14, T15, Function<T16, R>> curry15()",
		"public interface Applicative<F extends K1, Mu extends Applicative.Mu> extends Functor<F, Mu>",
		"std::reduce(std::execution::seq, v.cbegin(), v.cend())",
		"list.map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…).map(…)",
		"collection.filter(…).map(…).flatMap(…).filter(…).map(…).filter(…).forEach(…)",
		"forall void a n m. MonadEffect n => MonadAff m => MonadEffect m => Plus m => m a -> n (Tuple (m a) (m void))"
	]

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
	<h1>Functional</h1>
	{#each elements as element}
		<p class="code" style="animation-duration: {element.timing}s;">{element.text}</p>
	{/each}

	<div use:inview on:enter={createElements}></div>
</main>

<footer>
	(Functional programming is actually very cool. It's very satisfying to have a nice chain of maps, filters, and reduces; and lambdas are undeniably useful.
	<a href="https://github.com/Mojang/DataFixerUpper">This</a> scares me though.)
</footer>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
		overflow-x: hidden;
	}

	h1 {
		color: #c42525;
		text-transform: uppercase;
		font-size: 4em;
	}

	footer {
		position: sticky;
		bottom: 0;
		right: 0;
		padding: 0.2em;
		background-color: #55555577;
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

	@media (max-width: 640px) {
		h1 {
			font-size: 2em;
		}
	}

	@keyframes zipAcross {
		from { right: 100vw }
		to { right: -100vw }
	}
</style>