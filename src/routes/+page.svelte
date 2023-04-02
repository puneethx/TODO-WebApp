<script>
    let Todos = ["Hii","I am Puneeth","This is a project"]
</script>
<ol>
    {#each Todos as Todo}
    <li>{Todo}</li>
    {/each}
</ol>