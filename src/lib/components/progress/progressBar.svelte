<script>
	export let title;
	export let percentage;
	$: completeClass = title === 'Completed' ? 'bg-green-four' : 'bg-leaf-one';
</script>

<div>
	<div class="title">
		<p>{title}</p>
		<p>{percentage}%</p>
	</div>
	<div class="divclass">
		<div
			class="{completeClass} h-4 rounded-full transition-all duration-500 ease-out"
			style="width: {percentage}%"
		/>
	</div>
</div>


<style>
	.title{
		display: flex;
  		justify-content: space-between;
		font-size: 16px;
		font-weight: 400;
		color: #CBD5E1;
	}
	.divclass{
		margin-top: 5px;
		height: 4px;
		width: 100%;
		overflow: hidden;
		border-radius: 2px;
		background-color: #F7FAFC;
	}
</style>
