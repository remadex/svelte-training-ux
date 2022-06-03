<script>
  export let name;
  export let size = "1000TO";
  export let src;
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
    <button type="button" class="absolute inset-0 focus:outline-none">
      <span class="sr-only">View details for {name}</span>
    </button>
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
    >Delete</button
  >
</li>
