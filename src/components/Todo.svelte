<script>
  import { fade, fly } from "svelte/transition";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let id;
  export let title;
  export let completed;

  const onDelete = (e) => {
    e.preventDefault();
    dispatch("delete-todo", { id });
  };

  const onToggle = (e) => {
    e.preventDefault();
    dispatch("toggle-todo", { id });
  };
</script>

<li
  class="mb-6 flex justify-between px-3"
  in:fly={{ x: -100, duration: 600 }}
  out:fly={{ x: -100, duration: 300 }}>
  {title}
  <div>
    <button
      class="py-2 px-4 bg-indigo-300 hover:bg-indigo-200 text-indigo-800 mr-3
      rounded focus:outline-none"
      on:click={onToggle}>
      {completed ? 'uncomplete' : 'complete'}
    </button>
    <button
      class="py-2 px-4 focus:outline-none bg-red-300 hover:bg-red-200
      text-red-800 rounded"
      on:click={onDelete}>
      delete
    </button>
  </div>
</li>
