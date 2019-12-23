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
</script>

<main>
    <h1>{title}</h1>

    <AddTodo addTodo={addTodo} />
    <TodoList todoList={todoList} />
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
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