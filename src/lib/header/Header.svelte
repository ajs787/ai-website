<script>
	import { page } from '$app/stores';
	import logo from './logo.png';
</script>

<header>
	<div class="corner">
		<a href="https://kit.svelte.dev">
			<img src={logo} alt="SvelteKit" />
		</a>
	</div>

	<nav>
		<svg viewBox="0 0 2 3" aria-hidden="true">
			<path d="M0,0 L1,2 C1.5,3 1.5,3 2,3 L2,0 Z" />
		</svg>
		<ul>
			<li class:active={$page.url.pathname === '/'}><a sveltekit:prefetch href="/">Home</a></li>
			<li class:active={$page.url.pathname === '/about'}>
				<a sveltekit:prefetch href="/about">About</a>
			</li>
			<li class:active={$page.url.pathname === '/blog'}>
				<a sveltekit:prefetch href="/blog">Blog</a>
			</li>
			<li class:active={$page.url.pathname === '/team'}>
				<a sveltekit:prefetch href="/team">Team</a>
			</li>
			<li class:active={$page.url.pathname === '/resources'}>
				<a sveltekit:prefetch href="/resources">Resources</a>
			</li>
		</ul>
		<svg viewBox="0 0 2 3" aria-hidden="true">
			<path d="M0,0 L0,3 C0.5,3 0.5,3 1,2 L2,0 Z" />
		</svg>
	</nav>

	<div class="corner">
		<!-- TODO put something else here? github link? -->
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		height: 5.5em; 
		padding: 0 2rem;
	}

	.corner {
		width: 10em;
		height: 5em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 10em;
		height: 6em;
		object-fit: contain;
		
	}

	h2{
		font-size: 18px;
		font-weight:bolder;
	}

	nav {
		display: flex;
		justify-content: center;
		--background: rgba(255, 255, 255, 0.7);
	}

	nav svg:first-of-type {
	margin-right: -0.09em;
	}

	nav svg:last-of-type {
	margin-left: -0.09em;
	}

	svg {
		width: 2.5em;
		height: 3.5em;
		display: block;
	}

	path {
		fill: var(--background);
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3.5em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
		
	}

	li {
		position: relative;
		height: 100%;
	}

	li.active::before {
		--size: 8px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--accent-color);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 1.7em;
		color: var(--heading-color);
		font-weight: 700;
		font-size: 0.9rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--accent-color);
	}

	li.active a {
  		color: var(--accent-color);
	}

	:global([data-theme='dark']) nav {
		--background: rgba(104, 118, 153, 0.85); /* or just #000 for solid black */
	}
</style>
