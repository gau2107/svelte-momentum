<script>
import Todo from "./Todo.svelte";


    let todoInput = "";
    let todos = JSON.parse(localStorage.getItem("todos"));
    function onKeyup(e) {
        if(e.key === 'Enter') {
            let temp = {title: todoInput, checked: false};
            if(!todos || !todos.length)
                todos = [];
            todos = [...todos, temp];
            localStorage.setItem("todos", JSON.stringify(todos));
            todoInput = "";
        }
    }

    function deleteTodo(e) {
        todos.splice(e.detail, 1);
        localStorage.setItem("todos", JSON.stringify(todos));
        todos = [...todos];
    }
    function checkTodo(e) {
        console.log(todos[e.detail], e.detail, e);
        todos[e.detail].checked = true;
        localStorage.setItem("todos", JSON.stringify(todos));
    }
</script>
<div class="todo">
    <label for="">Todo</label>
    {#if todos}
    {#each todos as todo, i}
	    <Todo on:deleteTodo={deleteTodo} on:checkTodo={checkTodo} index={i} current={todo} />
	{/each}
    {/if}
<input class="todoInput" bind:value={todoInput} on:keyup={e => onKeyup(e)}>
</div>