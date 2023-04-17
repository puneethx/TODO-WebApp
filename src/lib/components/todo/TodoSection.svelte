<script>
	import TodoInput from '$lib/components/todo/TodoInput.svelte';
	import { todos } from '$lib/stores/todoStore';
</script>

<section class="mt-8 space-y-4">
	{#each $todos as todo (todo.id)}
		<TodoInput {todo} />
	{/each}
</section>