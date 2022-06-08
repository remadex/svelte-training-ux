<script>
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  import "./assets/css/style.css";

  let joke;
  let showAnswer = false;

  const getJoke = async () => {
    const res = await fetch("https://www.blagues-api.fr/api/random", {
      headers: {
        Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiMzI2NjkzNTc0ODY5NjQ3MzYxIiwibGltaXQiOjEwMCwia2V5IjoicEpXZEJtTU1uT3ZvNGFFOGFrZFdqMkVQU3dxZW5ycmtJUHJaUU5EeE1ORHhUclEySUciLCJjcmVhdGVkX2F0IjoiMjAyMi0wMy0yNFQxMzozMjoyOSswMDowMCIsImlhdCI6MTY0ODEyODc0OX0.mZkzOrX78rH4nEmE2u_ml2EdtD5i7_1fwmHf9bKyGfI`,
      },
    });
    joke = await res.json();
    showAnswer = false;
  };

  onMount(() => {
    setTimeout(async () => {
      await getJoke();
    }, 1000);
  });

  const refreshJoke = () => {
    joke = undefined;
    setTimeout(async () => {
      await getJoke();
    }, 1000);
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen overflow-hidden">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    {#if joke}
      <h2
        class="text-center text-4xl text-emerald-800"
        in:fly={{ x: 2000, duration: 1000 }}
        out:fade
      >
        {joke.joke}
      </h2>
      {#if !showAnswer}
        <button
          class="btn primary block mx-auto mt-4"
          in:fly={{ duration: 1000 }}
          out:fade
          on:click={() => (showAnswer = true)}
        >
          Montrer la réponse
        </button>
      {:else}
        <h3
          class="mt-4 text-center text-xl"
          in:fly={{ x: -2000, duration: 1000 }}
          out:fade
        >
          {joke.answer}
        </h3>
        <button
          class="btn primary block mx-auto mt-4"
          in:fly={{ x: 2000, duration: 1000 }}
          out:fade
          on:click={refreshJoke}
        >
          Une autre blague
        </button>
      {/if}
    {:else}
      <p in:fade out:fade class="text-center text-2xl">
        A la recherche d'une blague sur ta mère...
      </p>
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
