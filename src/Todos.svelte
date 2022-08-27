<script>
  import Todo from "./Todo.svelte";

  let todoInput = "";
  let editIndex = undefined;
  let todos = JSON.parse(localStorage.getItem("todos"));

  function onKeyup(e) {
    console.log(editIndex);
    if (e.key === "Enter") {
      if (editIndex >= 0) editTodo(e);
      else addTodo(e);
    }
  }

  function addTodo(e) {
    let temp = { title: todoInput, checked: false };
    if (!todos || !todos.length) todos = [];
    todos = [...todos, temp];
    localStorage.setItem("todos", JSON.stringify(todos));
    todoInput = "";
  }

  function editTodo(e) {
    todos[editIndex].title = todoInput;
    localStorage.setItem("todos", JSON.stringify(todos));
    editIndex = undefined;
  }

  function deleteTodo(e) {
    todos.splice(e.detail, 1);
    localStorage.setItem("todos", JSON.stringify(todos));
    todos = [...todos];
  }
  function checkTodo(e) {
    todos[e.detail].checked = true;
    localStorage.setItem("todos", JSON.stringify(todos));
  }
  function setEditForm(e) {
    let cur = todos[e.detail];
    todoInput = cur.title;
    editIndex = e.detail;
  }
</script>

<div class="todo">
  <label for="">Todo</label>
  {#if todos}
    {#each todos as todo, i}
      <Todo
        on:deleteTodo={deleteTodo}
        on:setEditForm={setEditForm}
        on:checkTodo={checkTodo}
        index={i}
        current={todo}
      />
    {/each}
  {/if}
  <input
    class="todoInput"
    bind:value={todoInput}
    on:keyup={(e) => onKeyup(e)}
  />
</div>
