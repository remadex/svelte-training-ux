<script>
  export let name, gender, imageUrl, free;
</script>

<div>
  <div
    class="grid grid-cols-4 p-3 pl-4 bg-gray-200 border-l-4 border-gray-500 rounded gap-x-2"
  >
    <div>
      <label
        for="name"
        class="block text-sm font-medium text-center text-gray-700">Name</label
      >
      <div class="mt-1">
        <input
          type="text"
          name="name"
          id="name"
          class="block w-full px-3 py-2 border-gray-300 rounded-sm shadow-sm focus:ring-indigo-500 focus:border-indigo-500"
          bind:value={name}
        />
      </div>
    </div>
    <div>
      <label
        for="imgUrl"
        class="block text-sm font-medium text-center text-gray-700"
        >Image url</label
      >
      <div class="mt-1">
        <input
          type="text"
          name="imgUrl"
          id="imgUrl"
          class="block w-full px-3 py-2 border-gray-300 rounded-sm shadow-sm focus:ring-indigo-500 focus:border-indigo-500"
          bind:value={imageUrl}
        />
      </div>
    </div>
    <div>
      <label
        for="imgUrl"
        class="block text-sm font-medium text-center text-gray-700">Genre</label
      >
      <div class="mt-2">
        <div class="flex justify-around">
          <div>
            <input
              type="radio"
              name="gender"
              id="male"
              value="male"
              bind:group={gender}
            />
            <label for="male">Male</label>
          </div>
          <div>
            <input
              type="radio"
              name="gender"
              id="female"
              value="female"
              bind:group={gender}
            />
            <label for="female">Female</label>
          </div>
          <div>
            <input
              type="radio"
              name="gender"
              id="binary"
              value="binary"
              bind:group={gender}
            />
            <label for="binary">Binary</label>
          </div>
        </div>
      </div>
    </div>
    <div class="flex items-center justify-center">
      <input
        id="free"
        name="free"
        type="checkbox"
        class="w-4 h-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500"
        bind:checked={free}
      />
      <label for="free" class="block ml-2 text-sm text-gray-900"> Free </label>
    </div>
  </div>
</div>
