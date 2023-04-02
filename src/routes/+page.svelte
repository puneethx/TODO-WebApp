<script>
    let todos = [
        {task:"Get books", isComplete: false, createdAt :"2021-08-06"},
        {task:"Get Tickets", isComplete: false, createdAt :"2021-08-06"},
        {task:"Get Bread", isComplete: true, createdAt :"2021-07-06"},
        ]
</script>
<ol>
    <h1>TODO</h1>
    {#each todos as todo}
    <li class:complete={todo.isComplete}>{todo.task}</li>
    {/each}
</ol>

<style>
    .complete{
        text-decoration: line-through;
    }
</style>