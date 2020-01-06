<script>
    import TodoList from './components/TodoList.svelte'
    import AddTodo from './components/AddTodo.svelte'

    export let title
    let nextId = 1
    let todoList = []

    $: console.log({ todoList })

    function addTodo(title) {
        todoList = [...todoList, {
            id: nextId,
            completed: false,
            title
        }]
        nextId = nextId + 1
    }

    function completeTodo(todoId) {
        console.log({todoId})
        const foundTodo = todoList.find(({id}) => id === todoId)

        console.log(foundTodo)

        if (foundTodo) {
            foundTodo.completed = true
            todoList = [...todoList, foundTodo]
            console.log(foundTodo)
        } else {
            console.log('TODO not found')
        }
        console.log(todoList)
    }
</script>

<main>
    <h1>{title}</h1>

    <div class="container">
        <AddTodo addTodo={addTodo} />
        <TodoList
                todoList={todoList}
                completeTodo={completeTodo}
        />
    </div>
</main>

<style type="text/scss">
    main {
        text-align: center;
        padding: 1em;
    }

    div.container {
        margin: 0 auto;
        width: 840px;
        font-family: "Comic Sans MS", sans-serif;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>