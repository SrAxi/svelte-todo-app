<script>
    import Todo from './components/Todo.svelte'

    export let title
</script>

<style type="text/scss">
    main {
        text-align: center;
        padding: 1em;
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

<main>
    <h1>{title}</h1>

    <Todo />
</main>

