<script>
	import { scale, fade, fly } from 'svelte/transition';

	let scroll = 0;
	function handleScroll() {
		scroll = window.scrollY / (document.body.scrollHeight - window.innerHeight);
	}
</script>

<svelte:head>
	<title>Resources</title>
	<meta name="description" content="Resources" />
</svelte:head>

<div class="content" in:fade={{duration: 300}}>
	<h1>Resources</h1>

	<p>
		<a href="https://github.com/Elias2660/Unified-bee-Runner">Github Repository</a> 
	</p>

</div>

<style>
	.content {
		width: 100%;
		max-width: var(--column-width);
		margin: 0rem auto 0 auto;
	}
</style>
