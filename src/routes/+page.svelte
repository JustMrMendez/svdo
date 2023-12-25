<script lang="ts">
	let todos = $state([
		{ text: 'Learn Svelte', done: false },
		{ text: 'Learn Tailwind', done: false },
		{ text: 'Learn TypeScript', done: false }
	]);

	function addTodo(event: KeyboardEvent) {
		if (event.key !== 'Enter') return;
		const target = event.target as HTMLInputElement;
	
		todos = [...todos, { text: target.value, done: false }];
		target.value = '';
		console.log(todos);
	}

	function removeTodo(todo: { text: string; done: boolean }) {
		todos = todos.filter(t => t.text !== todo.text);
	}

	$effect(() => {
		console.log('todos changed', todos);
	});

</script>

<div class="flex gap-3 p-4">
	<div class="input-group flex">
		<input type="text" class=" input rounded-r-none p-2" onkeydown={addTodo} />
		<button class="variant-ghost-primary btn btn-sm rounded-l-none">Add Task</button>
	</div>
</div>

<ol class="list p-2">
		{#each todos as { text, done }, i}
			<li class="flex gap-3 p-2">
				<label class="flex w-full items-center gap-3">
					<span>{i + 1}</span>
					<input type="checkbox" class="checkbox" bind:checked={done} />
					<input class="input flex-auto px-4 py-2" bind:value={text} />
				</label>
				<button class="variant-ghost-error btn btn-sm" onclick={() => todos.splice(i, 1)}
					>X</button
				>
			</li>
		{/each}
</ol>
