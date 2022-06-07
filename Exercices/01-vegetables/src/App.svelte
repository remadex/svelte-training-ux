<script>
  import "./assets/css/style.css";
  import Vegetables from "./Vegetables.svelte";
  let vegetables = [
    {
      name: "Radish",
      season: "Summer",
    },
    {
      name: "Onion",
      season: "Spring",
    },
    {
      name: "Carrot",
      season: "Summer",
    },
    {
      name: "Brussel sprouts",
      season: "Winter",
    },
    {
      name: "Cauliflower",
      season: "Winter",
    },
    {
      name: "Rocket",
      season: "Autumn",
    },
    {
      name: "Asparagus",
      season: "Spring",
    },
    {
      name: "Broccoli",
      season: "Summer",
    },
    {
      name: "Tomatoes ",
      season: "Autumn",
    },
    {
      name: "Pumpkin",
      season: "Autumn",
    },
  ];

  let show = false;
  let vegetable = {};

  const showList = () => {
    show = true;
    vegetable = {};
  };

  const showMeOne = () => {
    show = true;
    vegetable = vegetables[Math.floor(Math.random() * vegetables.length)];
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <div class="flex justify-around my-3">
      <button
        class="block p-4 font-bold text-white bg-yellow-600 rounded-lg"
        on:click={showList}>Show the list of vegetables</button
      >
      <button
        class="block p-4 font-bold text-white bg-blue-600 rounded-lg"
        on:click={showMeOne}>Show one vegetable</button
      >
    </div>
    <div>
      {#if show}
        {#if Object.keys(vegetable).length}
          <h2 class="text-3xl font-bold text-center">
            {vegetable.name} ({vegetable.season})
          </h2>
        {:else}
          <Vegetables {vegetables} />
        {/if}
      {/if}
    </div>
  </main>
</div>

<style>
  .animation-image {
    @apply cursor-pointer duration-200;
  }

  .animation-image:hover {
    @apply scale-75;
  }
</style>
