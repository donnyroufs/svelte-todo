<script>
  import AddTodo from "./AddTodo.svelte";
</script>

<div class="flex justify-between items-center">
  <h1 class="text-indigo-700 text-2xl font-bold my-12">Todos</h1>
  <AddTodo on:add-todo />
</div>
