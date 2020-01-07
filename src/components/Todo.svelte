<script>
    import TodoList from './TodoList.svelte'
    import AddTodo from './AddTodo.svelte'

    let nextId = 1
    let todoList = []

    function addTodo(title) {
        todoList = [...todoList, {
            id: nextId,
            completed: false,
            title
        }]
        nextId = nextId + 1
    }

    function completeTodo(todoId) {
        const foundTodo = todoList.find(({ id }) => id === todoId)

        if (foundTodo) {
            foundTodo.completed = true
            todoList = [...todoList, foundTodo]
        } else {
            console.log('TODO not found')
        }
    }

    function removeTodo(todoId) {
        todoList = [...todoList.filter(({ id }) => id !== todoId)]
    }
</script>

<div class="container">
    <AddTodo addTodo={addTodo} />
    <TodoList
            todoList={todoList}
            completeTodo={completeTodo}
            removeTodo={removeTodo}
    />
</div>

<style type="text/scss">
    div.container {
        margin: 0 auto;
        width: 840px;
        font-family: "Comic Sans MS", sans-serif;
    }
</style>