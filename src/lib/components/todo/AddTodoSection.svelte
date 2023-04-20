<script>
	import { addTodo } from '$lib/stores/todoStore';
</script>

<section class="container">
	<h3 class="h3">Checklist</h3>
	<button class="button" type="button" on:click={addTodo} > Add Task
		<svg
			class="svgclass"
			width="32"
			height="32"
			viewBox="0 0 32 32"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
		>
        <g clip-path="url(#clip0_35_391)">
            <path
                d="M14.4 14.4V8H17.6V14.4H24V17.6H17.6V24H14.4V17.6H8V14.4H14.4ZM16 32C7.1632 32 0 24.8368 0 16C0 7.1632 7.1632 0 16 0C24.8368 0 32 7.1632 32 16C32 24.8368 24.8368 32 16 32ZM16 28.8C19.3948 28.8 22.6505 27.4514 25.051 25.051C27.4514 22.6505 28.8 19.3948 28.8 16C28.8 12.6052 27.4514 9.3495 25.051 6.94903C22.6505 4.54857 19.3948 3.2 16 3.2C12.6052 3.2 9.3495 4.54857 6.94903 6.94903C4.54857 9.3495 3.2 12.6052 3.2 16C3.2 19.3948 4.54857 22.6505 6.94903 25.051C9.3495 27.4514 12.6052 28.8 16 28.8V28.8Z"
                fill="currentColor"
            />
        </g>
        <defs>
            <clipPath id="clip0_35_391">
                <rect width="32" height="32" fill="white" />
            </clipPath>
        </defs>
			
		</svg>
	</button>
</section>

<style>
	.container {
		display: flex;
		justify-content: space-between;
	}
	.h3{
		font-size: 1.25rem;
		font-weight: bold;
		color: #8c8c8c;
	}
	.button{
		display: flex;
		align-items: center;
		border-radius: 0.375rem; 
		border: 0.0625rem solid #d3d3d3;
		background-color: #fff7bf; 
		padding: 0.8rem; 
		font-size: 1.125rem; 
		font-weight: 600; 
		padding : 1%;
		color: #111827; 
		outline: 0.125rem solid #fff7bf; 
		outline-offset: 0.125rem;

	}
	.button:hover {
		color: #6e7039;
	}
	.button:focus-visible > *{
		color: var(--green-five); /* equivalent to focus-visible:text-green-five */
  		outline: 0.125rem solid var(--green-five);
	}
	.svgclass{
		margin-left: 0.75rem; /* equivalent to ml-3 */
  		height: 1rem; /* equivalent to h-4 */
  		width: 1rem; /* equivalent to w-4 */
  		color: var(--gray-five); /* equivalent to text-gray-five */
	}
	.svgclass:hover , .svgclass:focus-visible {
  		color: var(--green-five);
	}
</style>