<script>
	import TempConvertor from './TempConvertor.svelte';
  let Celsuis = $state(0);

  let Fahrenheit = $state(0);

  function convertToFahrenheit() {
    Fahrenheit = (Celsuis * 9) / 5 + 32;
  }

  function convertToCelsuis() {
    Celsuis = ((Fahrenheit - 32) * 5) / 9;
  }


</script>




<div class = "container flex flex-col items-center justify-center p-6 rounded-full m-5 bg-blue-800">


  <h1>Awad Temperature Convertor</h1>

   <div class="grid grid-cols-2 gap-4 m-aut p-4">

     <label for="Celsuis" class="p-2 border rounded"> Celsuis

       <input type="number" bind:value={Celsuis} placeholder="Celsius" class="p-2 border font-bold rounded" on:input={convertToFahrenheit} />
      </label>
    
      <label class="p-2 border rounded bg-blue-950" for="Fahrenheit">Fahrenheit

        <input type="number" bind:value={Fahrenheit} placeholder="Fahrenheit" class="p-2 bg-gray-900 border rounded" on:input={convertToCelsuis} />
      </label>

   </div>

</div>




