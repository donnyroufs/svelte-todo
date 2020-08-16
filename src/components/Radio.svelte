<script>
  export let options;
  export let label;
</script>

<label class="mr-4 mb-4 p-2 inline-block">
  <input
    type="radio"
    value={label}
    bind:group={options}
    selected={options === label} />
  {label}
</label>
