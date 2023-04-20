<script>
	import AddTodoSection from '$lib/components/todo/AddTodoSection.svelte';
	import TodoSection from '$lib/components/todo/TodoSection.svelte';
	import ProgressSection from '$lib/components/progress/progressSection.svelte';
	
</script>
<link href='https://fonts.googleapis.com/css?family=Poppins' rel='stylesheet'>
<!-- min-h-screen bg-olive-one p-0 selection:bg-green-two md:py-24 md:px-8 -->
<div class="divclass">
	<!-- "mx-auto min-h-screen max-w-none rounded-none bg-cream-four px-5 py-10 outline-none md:min-h-max md:max-w-[60rem] md:rounded-2xl md:px-8 md:outline md:outline-4 md:outline-offset-8 md:outline-cream-four" -->
	<main
		class="mainclass"
	>
		<h1 class="h1">Dashboard</h1>
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
		background-color: #cccd82;
		padding: 0;
		padding-top: 13.5%;
		font-family: "Poppins",sans-serif;
	}
	::selection {
		background-color: #fff9a0;
	}
@media screen and (min-width: 768px){
	.divclass{
		padding-top: 6rem;
		padding-bottom: 6rem;
		padding-left: 2rem;
		padding-right: 2rem;
	}
}
	.h1{
		color: black;
		font-family: "Poppins",sans-serif;
	}
.mainclass{
	margin-left: 6.8%;
	margin-right: 6.8%;
	max-width: none;
	border-radius: 10px;
	background-color: #f9f5e8;
	padding-left: 2.5%;
	padding-right: 2.5%;
	padding-top: 2.5%;
	padding-bottom: 5%;
	box-shadow: 
    0 0 0 6px #cccd82, 
    0 0 0 9px #FFFFFF; 
}

@media (min-height: 900px) {
  .mainclass{max-width: 60rem;
  min-height: max-content;
  border-radius: 2rem;
  padding-left: 8px;
  padding-right: 8px;
  outline: 4px solid #f9f5e8;
  outline-offset: 8px;}
}

h1{
font-size: 1.5rem;
font-weight: bold;
color: #888888;
}

.smalldiv{
	margin-top:10px
}
</style>