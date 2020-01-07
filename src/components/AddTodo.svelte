<script>
    let newTodo = ''
    export let addTodo

    function addTodoToList(e) {
        if (e.key === 'Enter') {
            addTodo(newTodo)
            newTodo = ''
        }
    }
</script>

<div class="new-todo">
    <label for="newTodo">Add a new TODO</label>
    <input
            id="newTodo"
            type="text"
            bind:value={newTodo}
            on:keydown={addTodoToList}
    />
</div>

<style type="text/scss">
    label {
        font-style: italic;
        color: #333333;
    }
</style>