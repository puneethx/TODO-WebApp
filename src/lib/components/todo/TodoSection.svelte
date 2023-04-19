<script>
	import TodoInput from '$lib/components/todo/TodoInput.svelte';
	import { todos } from '$lib/stores/todoStore';
</script>

<section class="todo-list">
	{#each $todos as todo (todo.id)}
		<TodoInput {todo} />
	{/each}
</section>

<style>
	.todo-list{
		margin-top: 2rem;
	}
</style>