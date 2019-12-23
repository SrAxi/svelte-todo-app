<script>
    export let todoList
</script>

<div class="todo-list">
    <ul>
        {#each todoList as todo (todo.id)}
            <li>{todo.title}</li>
        {/each}
    </ul>
</div>

<style>
    ul {
        list-style: none;
        padding: 20px
    }
</style>