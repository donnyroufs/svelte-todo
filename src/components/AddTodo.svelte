<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let value = "";

  const handleAddTodo = (e) => {
    e.preventDefault();
    if (value.length < 1) return;
    dispatch("add-todo", { title: value });
    value = "";
  };
</script>

<form class="flex" on:submit={handleAddTodo}>
  <input
    type="text"
    placeholder="add todo"
    bind:value
    class="mr-4 outline-none focus:shadow-outline focus:bg-blue-100 px-2 rounded" />
  <button
    class="py-2 px-4 bg-indigo-300 hover:bg-indigo-200 text-indigo-800 mr-3
    rounded focus:outline-none">
    Add Todo
  </button>
</form>
