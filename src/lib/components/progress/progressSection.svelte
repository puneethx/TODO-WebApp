<script>
    import ProgressBar from "./progressBar.svelte";
    import { todos } from "$lib/stores/todoStore";

    export let completePercentage = 0;
    export let progressPercentage = 0;

    $: totalCount = $todos.length;
    $: completeCount =  $todos.filter((todo) => todo.complete).length;
    $: progressCount = $todos.filter((todo) => !todo.complete).length;
    $: completePercentage = Math.round((completeCount / totalCount) * 100) || 0;
    $: progressPercentage = Math.round((progressCount / totalCount) * 100) || 0;
</script> 
<section>
    <h3>
        Progress
    </h3>
    <div>
        <!-- <ProgressBar title = "In Progress" percentage = {progressPercentage} />
        <ProgressBar title = "Completed" percentage = {completePercentage} /> -->
        <p>{progressPercentage}</p>
        <p>{completePercentage}</p>

    </div>
</section>