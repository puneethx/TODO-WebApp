<script>
    let todos = [
        {task:"Get books", isComplete: false, createdAt :"2021-08-06"},
        {task:"Get Tickets", isComplete: false, createdAt :"2021-08-06"},
        {task:"Get Bread", isComplete: true, createdAt :"2021-07-06"},
        ]

        let todo = {
            task:"",
            isComplete:false,
            createdAt:new Date(),
        };
        const addTodo = () => {
            todos = [...todos,todo];
        }

        $: console.table(todos);
</script>

<input type="text" bind:value={todo.task} />
<button on:click={addTodo}>Add</button>
<ol>
    {#each todos as todo}
    <li class:complete={todo.isComplete}>{todo.task}</li>
    {/each}
</ol>

<style>
    .complete{
        text-decoration: line-through;
    }
</style>