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

<div class="todos" in:fade={{ duration: 600 }}>
	<h1 in:fly={{ x: -100, duration: 500 }}>Todos</h1>

	<form
		class="new"
		action="/todos"
		method="post"
		use:enhance={{
			result: async ({ form }) => {
				form.reset();
			}
		}}
		in:fly={{ y: -20, duration: 500 }}
	>
		<input name="text" aria-label="Add todo" placeholder="+ tap to add a todo" />
	</form>

	{#each data.todos as todo (todo.uid)}
		<div
			class="todo"
			class:done={todo.done}
			transition:scale|local={{ start: 0.7 }}
			animate:flip={{ duration: 200 }}
		>
			<form
				action="/todos?_method=PATCH"
				method="post"
				use:enhance={{
					pending: ({ data }) => {
						todo.done = !!data.get('done');
					}
				}}
			>
				<input type="hidden" name="uid" value={todo.uid} />
				<input type="hidden" name="done" value={todo.done ? '' : 'true'} />
				<button class="toggle" aria-label="Mark todo as {todo.done ? 'not done' : 'done'}" />
			</form>

			<form class="text" action="/todos?_method=PATCH" method="post" use:enhance>
				<input type="hidden" name="uid" value={todo.uid} />
				<input aria-label="Edit todo" type="text" name="text" value={todo.text} />
				<button class="save" aria-label="Save todo" />
			</form>

			<form
				action="/todos?_method=DELETE"
				method="post"
				use:enhance={{
					pending: () => (todo.pending_delete = true)
				}}
			>
				<input type="hidden" name="uid" value={todo.uid} />
				<button class="delete" aria-label="Delete todo" disabled={todo.pending_delete} />
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
