<script>
	import { deleteTodo, toggleComplete, editTodo } from '$lib/stores/todoStore';
	
	export let todo;
	$: completeClass = todo.complete ? 'background-color: #4ade80' : 'background-color: #8dc63f';
</script>
<div class="maindiv">
	<div class="div2">
		<label for={`${todo.id}-checkbox`} class="labclass"></label>
		<input id={`${todo.id}-checkbox`} type="checkbox" checked={todo.complete} on:change={() => toggleComplete(todo.id)} class="inputclass" />
		<label for={`${todo.id}-text`} class="todoEdit">Edit todo</label>
		<input
			id={`${todo.id}-text`}
			type="text"
			placeholder="Enter a todo"
			value={todo.text}
			on:input={(e) => editTodo(todo.id, e.target.value)}
			class="inputTodo"
		/>
		<span
			class="{completeClass}"
		>
			{todo.complete ? 'Complete' : 'In Progress'}
		</span>
	</div>
	<button
		type="button"
		on:click={() => deleteTodo(todo.id)}
		class="deleteTodo"
	>
		<span class="deletespan">Delete todo</span>
		<svg
			class="svgclass"
			width="32"
			height="32"
			viewBox="0 0 32 32"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
		>
			<g clip-path="url(#clip0_35_392)">
				<path
					d="M24 6.4H32V9.6H28.8V30.4C28.8 30.8244 28.6314 31.2313 28.3314 31.5314C28.0313 31.8314 27.6243 32 27.2 32H4.8C4.37565 32 3.96869 31.8314 3.66863 31.5314C3.36857 31.2313 3.2 30.8244 3.2 30.4V9.6H0V6.4H8V1.6C8 1.17565 8.16857 0.768688 8.46863 0.468629C8.76869 0.168571 9.17565 0 9.6 0H22.4C22.8243 0 23.2313 0.168571 23.5314 0.468629C23.8314 0.768688 24 1.17565 24 1.6V6.4ZM25.6 9.6H6.4V28.8H25.6V9.6ZM18.2624 19.2L21.0912 22.0288L18.8288 24.2912L16 21.4624L13.1712 24.2912L10.9088 22.0288L13.7376 19.2L10.9088 16.3712L13.1712 14.1088L16 16.9376L18.8288 14.1088L21.0912 16.3712L18.2624 19.2ZM11.2 3.2V6.4H20.8V3.2H11.2Z"
					fill="currentColor"
				/>
			</g>
			<defs>
				<clipPath id="clip0_35_392">
					<rect width="32" height="32" fill="white" />
				</clipPath>
			</defs>
		</svg>
	</button>
</div>
<div class = "gap"></div>

<style>
	.gap{
		padding-top:10px;
	}
	.deletespan{
	position: absolute !important;
	clip: rect(1px, 1px, 1px, 1px);
	padding: 0 !important;
	border: 0 !important;
	height: 1px !important;
	width: 1px !important;
	overflow: hidden;
	white-space: nowrap;		
	}
	.deleteTodo{
		position: relative;
		margin-left: 1rem;
		align-items: center;
		justify-content: center;
		border-radius: 0.375rem;
		background-color: #f9f5e8;
		padding: 0.5rem;
	}
	.deleteTodo:hover{
		background-color: #4a5568;
	}
	.deleteTodo:focus{
		outline: none;
	}
	.deleteTodo.focus-visible{
		outline: 2px solid transparent;
		outline-offset: 2px;
		outline-color: #48bb78;
	}
	.completeClass{
		margin-left: 1.25rem;
		display: none !important;
		border-radius: 9999px;
		padding-top: 0.125rem;
  		padding-bottom: 0.125rem;
		padding-left: 0.5rem;
  		padding-right: 0.5rem;
		font-size: 0.875rem;
		font-weight: 400;
		color: #718096;
		color: #cbd5e0;
	}

	@media (min-width: 768px) {
		.md\:block {
			display: block !important;
		}
	}
	.maindiv{
		display: flex;
		align-items: center;
		justify-content: space-between;
		border-radius: 0.375rem;
		border: 2px solid #e5e7eb;
		padding-left: 5px;
		padding-right: 5px;
		padding-top: 4px;
		padding-bottom: 4px;
	}

	.divclass{
		display: flex;
		width: 100%;
		max-width: 32rem;
		align-items: center;
		justify-content: flex-start;
	}


	.labclass{
		padding: 0; 
		overflow: hidden;
		clip: rect(0, 0, 0, 0);
		white-space: nowrap;
		border: 0;
		width : auto;
		height : auto;
		padding-left: 10px;
	}

	.inputclass{
		height: 10px;
		width: 10px;
		border-radius: 50px;
		border: 1px solid #cbd5e0;
		background-color: #f3f4f6;
		color: #22c55e;
		outline: none;
		box-shadow: 0 0 0 2px rgba(34, 197, 94, 0.5);

	}
	.todoEdit{
		position: absolute;
		clip: rect(1px, 1px, 1px, 1px);
		padding: 0;
		border: 0;
		height: 1px;
		width: 1px;
		overflow: hidden;
	}
	.inputTodo{
		margin-left: 1.25rem;
		flex-grow: 1;
		width :50%;
		white-space: nowrap;
  		overflow: hidden;
  		text-overflow: ellipsis;
		border-radius: 0;
		border-left: none;
  		border-right: none;
		border-top: none;
		border-bottom-style: dashed;
		border-bottom-color: #cbd5e0;
		border-bottom-width: 1px;
		background-color: #fbf6ee;
		padding-left: 0;
  		padding-right: 0;
		padding-bottom: 0.25rem;
		font-size: 1rem;
		font-weight: 400;
		color: #4a5568;
	
	}
	.inputTodo::placeholder{
		color: #a0aec0;
	}
	.inputTodo:focus{
		border-color: #cbd5e0;
  		border-style: solid;
		outline: none;
		box-shadow: none;
	}
	.svgclass{
		height: 1.25rem;
		width: 1.25rem;
		color: #8795A1;
	}
	.svgclass:hover{
		color: #CBD5E1;
	}
</style>