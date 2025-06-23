<script>
	import { enhance } from '$lib/form';
	import { scale, fade, fly } from 'svelte/transition';
	import { flip } from 'svelte/animate';
	export let data;

	let scroll = 0;
	function handleScroll() {
		scroll = window.scrollY / (document.body.scrollHeight - window.innerHeight);
	}
</script>

<svelte:window on:scroll={handleScroll} />

<div class="content" in:fade={{duration: 300}}>
	<h1>Weekly Updates 2025</h1>

	<h2>
		Week 1 - Setup & Research
	</h2>
	<p>
		Brief Description blah blah
	</p>
	<div class="slides-container">
		<iframe 
			src="https://docs.google.com/presentation/d/e/2PACX-1vQTFh6yTD74YRJ9P6kxkVOYVn4hrsns4b2IoPE9KvP0poSl6dgx_XC-gLtT8eD5fiVWjIEdE0fdhn08/pubembed?start=false&loop=false&delayms=5000" 
			frameborder="0" 
			width="960" 
			height="569" 
			allowfullscreen="true" 
			mozallowfullscreen="true" 
			webkitallowfullscreen="true">
		</iframe>
	</div>


	<h2>
		Week 2 - Learning Linux & Running Code
	</h2>
	<p>
		Brief Description
	</p>
	<div class="slides-container">
		<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vStwU5axDB7yvryuUzbRg_bFEXDYdTm-EoJh9eCuSqbSGCBb2Hc5TqXWBphppufTQFH899PY9keGxbV/pubembed?start=false&loop=false&delayms=5000" 
		frameborder="0" 
		width="960" 
		height="569" 
		allowfullscreen="true" 
		mozallowfullscreen="true" 
		webkitallowfullscreen="true"></iframe>
	</div>


	<h2>
		Week 3 - 
	</h2>
	<p>
		Brief Description
		embed google slides presentation here
	</p>
	<div class="slides-container">
		<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTfSXqdKf-o5ZBvfNwXfGnPhLWRW7a76LjTOb-fZ6CeQGtW6LwR3Q2mjX3iN1oN6UTZ-iGPI8Kioc7V/pubembed?start=false&loop=false&delayms=5000" 
		frameborder="0" 
		width="960" 
		height="569" 
		allowfullscreen="true" 
		mozallowfullscreen="true" 
		webkitallowfullscreen="true"></iframe>
	</div>

	<h2>
		Week 4 - 
	</h2>
	<p>
		Brief Description
		embed google slides presentation here
	</p>
	<div class="slides-container">
		<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRx44851dXg3Bs5W3eYqo_5505RcvcrUVT42yMfo9msVQ71lM9BWsyXC34yvwM3ixJBwnyFrYZT3ufL/pubembed?start=false&loop=false&delayms=5000" frameborder="0" 
		width="960" 
		height="569" 
		allowfullscreen="true" 
		mozallowfullscreen="true" 
		webkitallowfullscreen="true"></iframe>
	</div>


</div>


<style>
	.scroll-progress {
		position: fixed;
		top: 0;
		left: 0;
		height: 4px;
		width: 100%;
		background: var(--accent-color);
		transform-origin: left center;
		z-index: 999;
		transition: transform 0.2s ease-out;
	}

	.slides-container{
		margin-bottom: 60px;
	}

	.new {
		position: sticky;
		top: 1rem;
		z-index: 10;
		background: var(--tertiary-color);
		backdrop-filter: blur(6px);
		padding: 0.5rem 0;
		border-radius: 8px;
		margin-bottom: 1rem;
	}

	h2{
		font-weight: bold;
		font-size: 20px;
	}
</style>
