<script>
	import AddTodoSection from '$lib/components/todo/AddTodoSection.svelte';
	import TodoSection from '$lib/components/todo/TodoSection.svelte';
	import ProgressSection from '$lib/components/progress/progressSection.svelte';
</script>
<!-- min-h-screen bg-olive-one p-0 selection:bg-green-two md:py-24 md:px-8 -->
<div class="divclass">
	<!-- "mx-auto min-h-screen max-w-none rounded-none bg-cream-four px-5 py-10 outline-none md:min-h-max md:max-w-[60rem] md:rounded-2xl md:px-8 md:outline md:outline-4 md:outline-offset-8 md:outline-cream-four" -->
	<main
		class="mainclass"
	>
		<h1>Dashboard</h1>
		<div class="smalldiv">
			<AddTodoSection />
			<TodoSection />
			<ProgressSection />
		</div>
	</main>
</div>

<style>
	.divclass{
		min-height: 100vh;
		background-color: #babf9e;
		padding: 0;
	}
	::selection {
  background-color: #b2d8b2;
}
/* @media screen and (min-width: 768px){
	padding-top: 6rem;
	padding-bottom: 6rem;

	padding-left: 2rem;
	padding-right: 2rem;
} */

.mainclass{
	margin-left: auto;
	margin-right: auto;
	min-height: 100vh;
	max-width: none;
	border-radius: none;
	background-color: #f9f5e8;
	padding-left: 5px;
	padding-right: 5px;
	padding-top: 10px;
	padding-bottom: 10px;
	outline: none;
}

/* @media (min-height: 100%) {
  max-width: 60rem;
  min-height: max-content;
  border-radius: 2rem;
  padding-left: 8px;
  padding-right: 8px;
  outline: 4px solid #f9f5e8;
  outline-offset: 8px;
} */

h1{
font-size: 1.5rem;
font-weight: bold;
color: #888888;
}

.smalldiv{
	margin-top:10px
}
</style>