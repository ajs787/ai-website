<script>
	import { enhance } from '$lib/form';
	import { scale, fade, fly } from 'svelte/transition';
	import { flip } from 'svelte/animate';

	let scroll = 0;
	function handleScroll() {
		scroll = window.scrollY / (document.body.scrollHeight - window.innerHeight);
	}
</script>

<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
	
</svelte:head>

<div class="content" in:fade={{duration: 300}}>
	<h1>The Project</h1>

	<p>
		The AI for Behavioural Discovery project aims to understand whether animal behaviour 
		is affected by exposure to EMF radiation using a machine learning and Convolutional Neural Networks (CNNs) approach. 
		We have conducted experiments on cockroaches, bees, and ants so far using AlexNet, achieving positive results with ants. The model was able to successfully classify field states between Positive, Negative and Off based only on behavioural changes of the ants.
	</p>

</div>

<style>
	.content {
		width: 100%;
		max-width: var(--column-width);
		margin: 0rem auto 0 auto;
	}
</style>
