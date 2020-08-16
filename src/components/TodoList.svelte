<script>
  import Radio from "./Radio.svelte";
  import Todo from "./Todo.svelte";

  export let todos;

  let options = "all";

  $: filtered = todos
    .filter((todo) => {
      if (options === "complete") {
        if (todo.completed) return todo;
      } else if (options === "incomplete") {
        if (!todo.completed) return todo;
      } else {
        return todo;
      }
    })
    .sort((a, b) => a.completed - b.completed);
</script>

<div class="border-b-2 border-gray-200">
  <Radio label="all" bind:options />
  <Radio label="complete" bind:options />
  <Radio label="incomplete" bind:options />
</div>

<ul class="mt-8">
  {#each filtered as todo}
    <Todo {...todo} on:toggle-todo on:delete-todo />
  {/each}
</ul>
