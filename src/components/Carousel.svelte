<script>
	import { onMount } from 'svelte';

	let carousel;

	onMount(() => {
		let initialMouseX;
		let initialTransform;

		const mouseDownHandler = function (e) {
			// Change the cursor and prevent user from selecting the text
			carousel.style.cursor = 'grabbing';

			// check if the carousel has been moved
			const transformValues = carousel.style.transform.match(/(..\d+)px/gm);

			if (transformValues !== null) {
				initialTransform = transformValues.reduce(
					(acc, curr) => acc + parseInt(curr.replace(/[\s(px)]/g, '')),
					0
				);
			} else {
				initialTransform = 0;
			}

			initialMouseX = e.clientX;

			document.addEventListener('mousemove', mouseMoveHandler);
			document.addEventListener('mouseup', mouseUpHandler);
		};

		const mouseMoveHandler = function (e) {
			// How far the mouse is from original position
			const dx = e.clientX - initialMouseX;

			// Scroll the element
			carousel.style.transform = `translateX(calc(-100% - 2rem + 50vw ${
				initialTransform < 0 ? '- ' + Math.abs(initialTransform) : '+ ' + initialTransform
			}px ${dx < 0 ? '- ' + Math.abs(dx) : '+ ' + dx}px))`;
		};

		const mouseUpHandler = function () {
			document.removeEventListener('mousemove', mouseMoveHandler);
			document.removeEventListener('mouseup', mouseUpHandler);

			carousel.style.cursor = 'grab';
		};

		carousel.addEventListener('mousedown', mouseDownHandler);
	});
</script>

<div class="carousel" bind:this={carousel}>
	<div class="track">
		<div class="wrapper"><img src="/projects/tbag.webp" alt="" /></div>
		<div class="wrapper"><img src="/projects/gif.webp" alt="" /></div>
		<div class="wrapper"><img src="/projects/blogg.webp" alt="" /></div>
		<div class="wrapper"><img src="/projects/environ.webp" alt="" /></div>
	</div>
	<svg class="arrow-right" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#000000">
		<path d="M0 0h24v24H0V0z" fill="none" />
		<path
			d="M5 13h11.17l-4.88 4.88c-.39.39-.39 1.03 0 1.42.39.39 1.02.39 1.41 0l6.59-6.59c.39-.39.39-1.02 0-1.41l-6.58-6.6c-.39-.39-1.02-.39-1.41 0-.39.39-.39 1.02 0 1.41L16.17 11H5c-.55 0-1 .45-1 1s.45 1 1 1z"
		/>
	</svg>
</div>

<style>
	.carousel {
		cursor: grab;
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		width: fit-content;
		/* ensures that the carousel is the full width of content, not the page. */
		transform: translateX(calc(-100% - 2rem + 50vw));
	}

	.arrow-right {
		margin-left: 2rem;
		height: 3rem;
		fill: hsl(var(--primary-200));
		transform: translateX(0);
		transition: transform 350ms cubic-bezier(0.5, -1, 0.5, 2);
		stroke: 4px;
		filter: drop-shadow(0.125rem 0.25rem 0.25rem rgba(0, 0, 0, 0.35));
	}

	.carousel:hover .arrow-right {
		transform: translateX(1rem);
	}

	.track {
		display: flex;
		gap: 2rem;
		height: 25rem;
	}

	.wrapper {
		position: relative;
		width: 100%;
		height: 100%;
		background: hsl(204, 20%, 85%);
		border-radius: 1rem;
	}

	.wrapper::before {
		content: '';
		position: absolute;
		right: 1.5rem;
		top: 50%;
		transform: translateY(-50%);
		height: 1.5rem;
		width: 1.5rem;
		border-radius: 50%;
		background-color: hsl(var(--light));
		box-shadow: inset 0.25rem 0.25rem 0.5rem hsl(var(--primary-200), 0.35);
	}

	.wrapper:last-of-type::after {
		right: -4rem;
		width: 7rem;
	}

	.wrapper::after {
		content: '';
		position: absolute;
		z-index: 1;
		right: -2rem;
		top: calc(50%);
		transform: translateY(-50%);
		height: 4px;
		width: 5rem;
		background-color: hsl(var(--primary-200));
		background: linear-gradient(
			90deg,
			black 0%,
			hsl(var(--primary-200)) 22%,
			hsl(var(--primary-200)) 100%
		);
		box-shadow: 0.125rem 0.25rem 0.25rem rgba(0, 0, 0, 0.35);
	}

	.wrapper:nth-of-type(1):after {
		filter: hue-rotate(60deg);
	}
	.wrapper:nth-of-type(2):after {
		filter: hue-rotate(120deg);
	}
	.wrapper:nth-of-type(3):after {
		filter: hue-rotate(180deg);
	}

	img {
		display: block;
		pointer-events: none;
		height: 100%;
		box-shadow: 0.5rem 0.5rem 1rem hsl(var(--primary-200), 0.15);
		aspect-ratio: 16 / 9;
		border-radius: 1rem;
		border: solid white 0.25rem;
	}
</style>
