<script>
	export let title;
	export let percentage;
	$: completeClass = title === 'Completed' ? "background-color:DodgerBlue;" : "background-color:DodgerBlue;";
</script>

<div>
	<div class="title">
		<p>{title}</p>
		<p>{percentage}%</p>
	</div>
	<div class="divclass">
		<div
			class="{completeClass}"
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
		background-color: #c7c7c7;
	}
	.completeClass{
		height: 4px;
		border-radius: 9999px;
		transition: all 500ms ease-out;	
	}
</style>
