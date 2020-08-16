<script>
  import Todo from "./lib/Todo";
  import Header from "./components/Header.svelte";
  import TodoList from "./components/TodoList.svelte";
  import Progress from "./components/Progress.svelte";
  import { onMount } from "svelte";

  let todos = [];

  $: getPercentage = () => {
    let completed = todos.filter((todo) => todo.completed);
    return (completed.length / todos.length) * 100;
  };

  onMount(async () => {
    const res = await fetch(
      `https://jsonplaceholder.typicode.com/todos?_limit=5`
    );
    const data = await res.json();
    todos = data.map((todo) => new Todo(todo));
  });

  const handleToggle = (event) => {
    const { id } = event.detail;
    const newTodos = todos.map((todo) => {
      if (todo.id === id) {
        todo.toggle();
      }
      return todo;
    });
    todos = newTodos;
  };

  const handleDelete = (event) => {
    const { id } = event.detail;
    const newTodos = todos.filter((todo) => todo.id !== id);
    todos = newTodos;
  };

  const addTodo = (event) => {
    const { title } = event.detail;
    const newTodo = new Todo({ id: todos.length + 1, title });
    todos = [newTodo, ...todos];
  };
</script>

<div class="mx-auto w-1/3">
  <Header on:add-todo={addTodo} />
  <TodoList
    {todos}
    on:toggle-todo={handleToggle}
    on:delete-todo={handleDelete} />
  <Progress percentage={getPercentage()} />
</div>
