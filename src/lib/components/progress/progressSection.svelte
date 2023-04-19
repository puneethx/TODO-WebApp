<script>
    import ProgressBar from "$lib/components/progress/progressBar.svelte";
    import { todos } from "$lib/stores/todoStore";

    export let completePercentage = 0;
    export let progressPercentage = 0;

    $: totalCount = $todos.length;
    $: completeCount =  $todos.filter((todo) => todo.complete).length;
    $: progressCount = $todos.filter((todo) => !todo.complete).length;
    $: completePercentage = Math.round((completeCount / totalCount) * 100) || 0;
    $: progressPercentage = Math.round((progressCount / totalCount) * 100) || 0;
</script> 
<section class="section">
    <h3 class = "h3">
        Progress
    </h3>
    <div class="element">
        <ProgressBar title = "In Progress" percentage = {progressPercentage} />
        <br>
        <ProgressBar title = "Completed" percentage = {completePercentage} />
    </div>
</section>

<style>
    .element {
  margin-top: 8px;
}
.h3{
    font-size: 1.25rem;
}
.section{
    margin-top: 2em;
}
</style>