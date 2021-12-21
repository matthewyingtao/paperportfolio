<script>
	import NavBar from './../components/NavBar.svelte';
	import Carousel from '../components/Carousel.svelte';
</script>

<section class="hero">
	<div class="title">
		<h4>Front-end developer</h4>
		<h1>Matthew Tao</h1>
	</div>
	<NavBar />
	<Carousel />
</section>

<style>
	.hero {
		position: relative;
		min-height: 100vh;
		padding: 2rem 2rem 2rem 4rem;
		overflow-x: hidden;
	}

	.title {
		margin-top: max(2rem, 12.5vh);
		margin-bottom: 2rem;
	}

	.title h4 {
		color: hsl(var(--primary-300), 0.6);
		font-weight: 400;
		font-style: italic;
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	.title h1 {
		font-size: 4.5rem;
		line-height: 0.75;
	}
</style>
