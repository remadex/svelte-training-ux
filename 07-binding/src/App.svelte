<script>
  import "./assets/css/style.css";
  import CardDetail from "./CardDetail.svelte";
  import FormDetail from "./FormDetail.svelte";

  const humanDetail = {
    name: "Mark Henry",
    gender: "binary",
    imageUrl: "https://picsum.photos/900/900",
    free: false,
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
    <FormDetail
      bind:name={humanDetail.name}
      bind:gender={humanDetail.gender}
      bind:imageUrl={humanDetail.imageUrl}
      bind:free={humanDetail.free}
    />
    <CardDetail {...humanDetail} />
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
