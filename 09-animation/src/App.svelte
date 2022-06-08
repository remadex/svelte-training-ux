<script>
  import { fly, fade } from "svelte/transition";
  import { draw } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  import "./assets/css/style.css";

  let name = "";
  $: disabled = name.length > 3 ? false : true;

  let deathList = [];
  const killEvent = () => {
    deathList = [...deathList, name];
    name = "";
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- CONTENU ICI -->
    <h1 class="title primary">Death note</h1>
    <form class="my-4 shadow-sm p-8" on:submit|preventDefault={killEvent}>
      <div class="form-control input">
        <label for="name"> Ajouter le nom de quelqu'un </label>
        <input type="text" id="name" bind:value={name} />
      </div>
      <button type="submit" {disabled} class="btn primary mt-4">Ajouter</button>
    </form>
    <div class="bg-black text-white shadow-md rounded-md p-8">
      {#each deathList as death}
        <p
          class="mt-2 text-2xl text-center"
          in:fly={{ y: -200, duration: 1000, delay: 100 }}
          out:fade
        >
          {death}
        </p>
        <!-- <svg viewBox="0 0 5 5" class="w-16" xmlns="http://www.w3.org/2000/svg">
          <path
            transition:draw={{ duration: 5000, delay: 500, easing: quintOut }}
            d="M2 1 h1 v1 h1 v1 h-1 v1 h-1 v-1 h-1 v-1 h1 z"
            fill="none"
            stroke="cornflowerblue"
            stroke-width="0.1px"
            stroke-linejoin="round"
          />
        </svg> -->
      {:else}
        <p class="text-3xl text-center" in:fade>No one to kill</p>
      {/each}
      {#if deathList.length}
        <button
          class="btn cancel mt-8 mx-auto block"
          on:click={() => (deathList = [])}>Save their life</button
        >
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
