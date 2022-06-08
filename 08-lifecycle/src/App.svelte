<script>
  import { afterUpdate, beforeUpdate, onMount } from "svelte";

  import "./assets/css/style.css";

  let quote;

  onMount(() => {
    setTimeout(async () => {
      const res = await fetch("https://api.kanye.rest/");
      quote = (await res.json()).quote;
    }, 1000);
  });

  const refreshQuote = () => {
    quote = "";
    setTimeout(async () => {
      const res = await fetch("https://api.kanye.rest/");
      quote = (await res.json()).quote;
    }, 1000);
  };

  beforeUpdate(() => {
    console.log("avant que le component se regènére");
  });

  afterUpdate(() => {
    console.log("après que le component se regènére");
  });
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- CONTENU ICI -->
    {#if quote}
      <p class="my-4 ml-2 italic font-bold">"{quote}"</p>
      <button
        class="px-4 py-2 text-sm font-bold text-white bg-emerald-600 duration-200 rounded-lg hover:bg-emerald-900"
        on:click={refreshQuote}
      >
        Refresh the quote
      </button>
    {:else}
      <p class="text-4xl">Loading...</p>
    {/if}
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
