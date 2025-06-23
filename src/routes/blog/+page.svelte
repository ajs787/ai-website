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
	<h1>Weekly Updates</h1>

	<h2>
		Week 1 - 
	</h2>

	<p>
		Brief Description
		embed google slides presentation here
	</p>


	<h2>
		Week 2 - 
	</h2>
	
	<p>
		Brief Description
		embed google slides presentation here
	</p>


	<h2>
		Week 3 - 
	</h2>
	<p>
		Brief Description
		embed google slides presentation here
	</p>

	<h2>
		Week 4 - 
	</h2>
	<p>
		Brief Description
		embed google slides presentation here
	</p>

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
