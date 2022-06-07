<script>
  import { createEventDispatcher } from "svelte";

  export let id;
  export let name;
  export let size = "1000TO";
  export let src;
  const dispatch = createEventDispatcher();

  const deleteThisFuckingImage = () => {
    dispatch("deleteImg", id);
  };
</script>

<li class="relative">
  <div
    class="block w-full overflow-hidden bg-gray-100 rounded-lg group aspect-w-10 aspect-h-7 focus-within:ring-2 focus-within:ring-offset-2 focus-within:ring-offset-gray-100 focus-within:ring-indigo-500"
  >
    <img
      {src}
      alt=""
      class="object-cover w-full pointer-events-none group-hover:opacity-75"
    />
  </div>
  <p
    class="block mt-2 text-sm font-medium text-gray-900 truncate pointer-events-none"
  >
    {name}
  </p>
  <p class="block text-sm font-medium text-gray-500 pointer-events-none">
    {size}
  </p>
  <button
    class="block px-2 py-1 mx-auto text-sm text-right text-white duration-200 bg-red-500 hover:bg-red-300"
    on:click={deleteThisFuckingImage}>Delete</button
  >
</li>
