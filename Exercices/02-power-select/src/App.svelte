<script>
  // @ts-nocheck

  import "./assets/css/style.css";
  import ListElement from "./ListElement.svelte";
  import { clickOutside } from "./clickOutside.js";

  let showSelect = false;
  let currentCountry;
  let countries = [
    {
      id: 1,
      src: "https://countryflagsapi.com/png/be",
      country: "Belgium",
    },
    {
      id: 2,
      src: "https://countryflagsapi.com/png/it",
      country: "Italy",
    },
    {
      id: 3,
      src: "https://countryflagsapi.com/png/fr",
      country: "France",
    },
    {
      id: 4,
      src: "https://countryflagsapi.com/png/ga",
      country: "Gabon",
    },
    {
      id: 5,
      src: "https://countryflagsapi.com/png/us",
      country: "United State",
    },
    {
      id: 6,
      src: "https://countryflagsapi.com/png/sr",
      country: "Suriname",
    },
  ];

  const handleSetCountry = (e) => {
    currentCountry = countries.find((c) => c.id === e.detail);
    showSelect = false;
  };
  const handleClickOutside = () => {
    showSelect = false;
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <div class="relative inline-block text-left">
      <div>
        <button
          type="button"
          class="inline-flex justify-center w-full rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none"
          on:click={() => (showSelect = !showSelect)}
        >
          {#if currentCountry}
            <span class="flex items-center">
              <img
                src={currentCountry.src}
                alt={currentCountry.country}
                class="w-6 mr-4"
              />
              {currentCountry.country}
            </span>
          {:else}
            Select country
          {/if}
          <svg
            class="-mr-1 ml-2 h-5 w-5"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
      </div>
      {#if showSelect}
        <div
          class="origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 focus:outline-none"
          use:clickOutside
          on:click_outside={handleClickOutside}
        >
          {#each countries as country}
            <ListElement {...country} on:setCountry={handleSetCountry} />
          {/each}
        </div>
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
