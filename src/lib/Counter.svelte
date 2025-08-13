<script>
  let count = $state(0);

  
</script>



<div class="container flex flex-col items-center justify-center p-6 rounded-full m-5 bg-fuchsia-900">

  <h1 class="text-3xl font-bold mb-4">Awad Counter</h1>
  
  <h2 class="text-3xl font-bold mb-4" >Count: {count}</h2>
  
  <button onclick={() => count++} class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"> 
    
  Count
</button>

  </div>
