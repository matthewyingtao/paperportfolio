<nav>
	<a href="#content" class="link">
		<span>Projects</span>
		<!-- down arrow -->
		<svg
			class="arrow"
			xmlns="http://www.w3.org/2000/svg"
			width="24"
			height="24"
			viewBox="0 0 24 24"
		>
			<path d="M7 10l5 5 5-5z" />
		</svg>
	</a>
	<a href="#content" class="link">
		<span>About Me</span>
		<svg
			class="arrow"
			xmlns="http://www.w3.org/2000/svg"
			width="24"
			height="24"
			viewBox="0 0 24 24"
		>
			<path d="M7 10l5 5 5-5z" />
		</svg>
	</a>
	<a href="#content" class="link">
		<span>Contact</span>
		<svg
			class="arrow"
			xmlns="http://www.w3.org/2000/svg"
			width="24"
			height="24"
			viewBox="0 0 24 24"
		>
			<path d="M7 10l5 5 5-5z" />
		</svg>
	</a>
</nav>

<style>
	nav {
		display: flex;
		gap: 2rem;
		border-radius: 1rem;
		margin-top: 4rem;
	}

	nav a {
		text-decoration: none;
	}

	.link {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.link span {
		color: hsl(var(--primary-200), 0.85);
		font-size: 1.25rem;
		font-style: italic;
		transition: color 250ms ease-in-out, transform 250ms ease-in-out;
	}

	.link:hover span {
		color: hsl(var(--primary-200), 0.65);
		transform: translateY(-0.25rem);
	}

	.arrow {
		fill: hsl(var(--primary-200), 0.65);
		opacity: 0;
		transform: translateY(-0.75rem);
		transition: opacity 250ms cubic-bezier(0.5, -1, 0.5, 2),
			transform 250ms cubic-bezier(0.5, -1, 0.5, 2);
	}

	.link:hover .arrow {
		opacity: 1;
		transform: translateY(-0.25rem);
	}
</style>
