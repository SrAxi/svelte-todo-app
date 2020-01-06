<script>
    export let todoList
    export let completeTodo

    function complete(id) {
        completeTodo(id)
    }
</script>

<div class="todo-list">
    <ul>
        {#each todoList as todo (todo.id)}
            <li>
                <span
                        class={todo.completed ? 'completed todo-title' : 'todo-title'}
                >{todo.title}</span>
                <a class="remove-btn">remove</a>
                |<a class="complete-btn" on:click|preventDefault={() => complete(todo.id)}>complete</a>
            </li>
        {/each}
    </ul>
</div>

<style type="text/scss">
    div.todo-list {
        margin: 0 auto;
        width: 600px;
    }

    ul {
        list-style: none;
        padding: 20px;

        li {
            margin-bottom: 1em;

            &:hover {
                cursor: default;
            }

            span {
                &.todo-title {
                    border: #666666 solid 1px;
                    border-radius: 1em;
                    padding: 5px 8px;
                    font-size: 1em;
                }

                &.completed {
                    text-decoration: underline;
                }
            }


            a {
                text-decoration: none;
                font-size: 0.8em;
                padding: 2px 0;
                margin: 0 5px;
                font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;

                &:hover {
                    cursor: pointer;
                }

                &.remove-btn {
                    color: #ff3e00;
                }

                &.complete-btn {
                    color: green;
                }
            }
        }
    }
</style>