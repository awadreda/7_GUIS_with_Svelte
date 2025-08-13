<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import TempConvertor from './lib/TempConvertor.svelte';
  import BookFlight from './lib/BookFlight.svelte';
  import Timer from './lib/Timer.svelte';
</script>

<main>

  <div class ="container flex flex-col items-center justify-center min-h-screen ">
  <h1 class="text-3xl font-bold mb-4">Awad Play with Svelte</h1>
    
    
    <!-- <Counter />
    <TempConvertor  />
    <BookFlight /> -->

    <Timer /> 
  </div>
</main>

