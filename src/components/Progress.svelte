<script>
  export let percentage;
</script>

<div class="w-full mt-12">
  <div class="mb-2">Progress</div>
  <div class="shadow w-full bg-grey-light">
    <div
      class="bg-indigo-400 text-xs leading-none py-1 text-center text-white
      tranistion-all duration-500 ease-in-out"
      style="width: {Math.trunc(percentage) || 0}%">
      {Math.trunc(percentage)}%
    </div>
  </div>
</div>
