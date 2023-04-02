<script>
    let Todos = ["Hii","I am Puneeth","This is a project"]
</script>
<ol>
    <h1>TODO</h1>
    {#each Todos as Todo}
    <li>{Todo}</li>
    {/each}
</ol>