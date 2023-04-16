<script>
	import { addTodo } from '../../store/TodoStore';
</script>

<section class="flex justify-between">
	<h3 class="text-xl font-bold text-gray-three">Checklist</h3>
	<button
		class="group flex items-center rounded-md border-cream-four bg-green-one px-6 py-3 text-lg font-semibold text-gray-five outline outline-2 outline-offset-2 outline-green-one hover:text-green-five focus-visible:text-green-five focus-visible:outline-green-five"
		type="button"
		on:click={addTodo}
	>
		Add Task
		<svg
			class="ml-3 h-4 w-4 text-gray-five group-hover:text-green-five group-focus-visible:text-green-five"
			width="32"
			height="32"
			viewBox="0 0 32 32"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
		>
			
		</svg>
	</button>
</section>