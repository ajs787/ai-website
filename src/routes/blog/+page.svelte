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

<div class="scroll-progress" style="transform: scaleX({scroll})"></div>

<div class="blog" in:fade={{ duration: 600 }}>
	<h1 in:fly={{ x: -100, duration: 500 }}>Blog</h1>

	<form
		class="new"
		action="/blog"
		method="post"
		use:enhance={{
			result: async ({ form }) => {
				form.reset();
			}
		}}
		in:fly={{ y: -20, duration: 500 }}
	>
		<input name="text" aria-label="Add blg" placeholder="+ tap to add a blg" />
	</form>

	{#each data.blog as blg (blog.uid)}
		<div
			class="blg"
			class:done={blg.done}
			transition:scale|local={{ start: 0.7 }}
			animate:flip={{ duration: 200 }}
		>
			<form
				action="/blog?_method=PATCH"
				method="post"
				use:enhance={{
					pending: ({ data }) => {
						blg.done = !!data.get('done');
					}
				}}
			>
				<input type="hidden" name="uid" value={blg.uid} />
				<input type="hidden" name="done" value={blg.done ? '' : 'true'} />
				<button class="toggle" aria-label="Mark blg as {blg.done ? 'not done' : 'done'}" />
			</form>

			<form class="text" action="/blgs?_method=PATCH" method="post" use:enhance>
				<input type="hidden" name="uid" value={blg.uid} />
				<input aria-label="Edit blg" type="text" name="text" value={blg.text} />
				<button class="save" aria-label="Save blg" />
			</form>

			<form
				action="/blgs?_method=DELETE"
				method="post"
				use:enhance={{
					pending: () => (blg.pending_delete = true)
				}}
			>
				<input type="hidden" name="uid" value={blg.uid} />
				<button class="delete" aria-label="Delete blg" disabled={blg.pending_delete} />
			</form>
		</div>
	{/each}
</div>

<div class="extras">
  <h2>What's next?</h2>
  <p>This section can contain your notes, project goals, or even motivational quotes 🧠💡</p>

  <div class="footer-links">
    <a href="#hero">Back to Top</a>
    <a href="/about">Learn More</a>
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
</style>
