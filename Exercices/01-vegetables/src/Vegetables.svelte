<script>
  export let vegetables;
</script>

{#each vegetables as { name, season }, index}
  <p class="mt-1 ml-2">{index + 1}. {name} ({season})</p>
{/each}
