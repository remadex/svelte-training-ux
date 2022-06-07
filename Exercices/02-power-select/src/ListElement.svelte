<script>
  import { createEventDispatcher } from "svelte";
  export let id, country, src;
  const dispatch = createEventDispatcher();
</script>

<div
  class="flex items-center px-4 py-2 text-sm text-gray-700 cursor-pointer hover:bg-gray-100 first:rounded-t-md last:rounded-b-md"
  on:click={() => dispatch("setCountry", id)}
>
  <img {src} alt="Logo of {country}" class="w-6 mr-4" />
  {country}
</div>
