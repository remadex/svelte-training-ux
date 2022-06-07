<script>
  export let name, gender, imageUrl, free;
</script>

<div class="border border-gray-200 rounded shadow-sm mt-4">
  <img
    src={imageUrl}
    alt="Picture of {name}"
    class="object-cover object-center w-full h-64 rounded-t"
  />
  <div class="flex flex-col items-center py-8">
    <h2 class="text-3xl font-bold text-gray-400">{name}</h2>
    <h3 class="text-xl font-bold text-indigo-300">{gender}</h3>
    <p class="mt-4 text-2xl font-bold">
      {free ? "Free" : "Not free"} for tonight
    </p>
  </div>
</div>
