<script>
  import format from "date-fns/format";
  import "./assets/css/style.css";
  import Kid from "./Kid.svelte";

  let user = { loggedIn: false };
  let logs = [];
  const toggleLogin = () => {
    user.loggedIn = !user.loggedIn;
    logs = [
      ...logs,
      {
        isConnect: user.loggedIn,
        time: format(new Date(), "HH:mm:ss"),
      },
    ];
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
    <Kid password="goulalustre" />
    <Kid />
    {#if user.loggedIn}
      <button
        class="px-4 py-2 rounded shadow bg-red-600 text-white duration-200 hover:bg-red-900"
        on:click={toggleLogin}>Log out</button
      >

      {#if logs}
        {#each logs as { isConnect, time }, index}
          <p class="mt-2 ml-4">
            {index + 1}. {isConnect ? "Connexion" : "Déconnexion"} à {time}
          </p>
        {/each}
      {/if}
    {:else}
      <button
        class="px-4 py-2 rounded shadow bg-blue-600 text-white duration-200 hover:bg-blue-900"
        on:click={toggleLogin}>Log in</button
      >
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
