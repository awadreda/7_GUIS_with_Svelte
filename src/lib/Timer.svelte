






<script lang="ts">
  import { onDestroy, onMount } from "svelte";
  import { fade } from "svelte/transition";



let elapsedTime: number = 0;
let duration: number = 10; // Duration in seconds
let running: boolean = true;
let timerInterval:ReturnType<typeof setInterval>;


  function startTimer():void {
    clearInterval(timerInterval);
    timerInterval = setInterval(() =>{
      if(running) {
        elapsedTime +=1;
        if(elapsedTime >= duration){
          elapsedTime= duration;
          running = false; // Stop the timer when duration is reached
        }
      }
    },500);
  }


    function updateDuration(value :number):void {
      duration =value;
      running= elapsedTime < duration;
    }

    function restartTimer():void {
      elapsedTime=0;
      running = true;
    }

    onMount(() => {
      startTimer();
    });

    onDestroy(() => {
      clearInterval(timerInterval);
    });



</script>


<style>
  .progress {
    width: 100%;
    height: 20px;
    appearance: none;
  }
  progress::-webkit-progress-bar {
    background-color: #e5e7eb;
    border-radius: 10px;
  }
  progress::-webkit-progress-value {
    background-color: #3b82f6;
    border-radius: 10px;
    transition: width 0.3s ease;
  }
</style>





<div class="max-w-lg mx-auto p-6 bg-white shadow-lg rounded-xl">
  <h1 class="text-3xl font-bold mb-6 text-center text-blue-600">Awad Timer</h1>

  <div class="mb-4" in:fade>
    <progress
      class="progress w-full h-6"
      value={elapsedTime}
      max={duration}
    ></progress>
  </div>

  <div class="flex justify-between items-center mb-4">
    <span class="text-lg font-mono text-black">{elapsedTime}s</span>
    <span class="text-sm text-gray-600">/ {duration}s</span>
  </div>

  <input 
    type="range" 
    min="1" 
    max="60" 
    value={duration}
    on:input={(e: Event) => updateDuration(parseFloat((e.target as HTMLInputElement).value))}
    class="w-full accent-blue-500 cursor-pointer mb-4" 
  />

  <button 
    on:click={restartTimer} 
    class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg shadow"
  >
    Reset
  </button>

  
</div>





<!-- 
<script lang="ts">
  import { onMount, onDestroy } from 'svelte';
  import { fade, scale } from 'svelte/transition';

  let elapsedTime: number = 0;
  let duration: number = 10;
  let running: boolean = true;
  let timerInterval: ReturnType<typeof setInterval>;

  // تشغيل المؤقت
  function startTimer(): void {
    clearInterval(timerInterval);
    timerInterval = setInterval(() => {
      if (running) {
        elapsedTime += 1;
        if (elapsedTime >= duration) {
          elapsedTime = duration;
          running = false; // وقف المؤقت
        }
      }
    }, 500);
  }

  // تحديث المدة من السلايدر
  function updateDuration(value: number): void {
    duration = value;
    running = elapsedTime < duration;
  }

  // إعادة التايمر
  function resetTimer(): void {
    elapsedTime = 0;
    running = true;
  }

  // عند تركيب المكون
  onMount(() => {
    startTimer();
  });

  // تنظيف المؤقت عند إزالة المكون
  onDestroy(() => {
    clearInterval(timerInterval);
  });
</script>

<style>
  .progress {
    width: 100%;
    height: 20px;
    appearance: none;
  }
  progress::-webkit-progress-bar {
    background-color: #e5e7eb;
    border-radius: 10px;
  }
  progress::-webkit-progress-value {
    background-color: #3b82f6;
    border-radius: 10px;
    transition: width 0.3s ease;
  }
</style>

<div class="max-w-lg mx-auto p-6 bg-white shadow-lg rounded-xl">
  <h1 class="text-3xl font-bold mb-6 text-center text-blue-600">Awad Timer</h1>

  <div class="mb-4" in:fade>
    <progress
      class="progress w-full h-6"
      value={elapsedTime}
      max={duration}
    ></progress>
  </div>

  <div class="flex justify-between items-center mb-4">
    <span class="text-lg font-mono text-black " in:scale>{elapsedTime}s</span>
    <span class="text-sm text-gray-600">/ {duration}s</span>
  </div>

  <input 
    type="range" 
    min="1" 
    max="60" 
    value={duration}
    on:input={(e: Event) => updateDuration(parseFloat((e.target as HTMLInputElement).value))}
    class="w-full accent-blue-500 cursor-pointer mb-4" 
  />

  <button 
    on:click={resetTimer} 
    class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg shadow"
    in:fade
  >
    Reset
  </button>
</div>
 -->


<!-- 



<script>


let elapsedTime = $state(0);

let duration = $state(10); // Duration in seconds

let timerInterval=0;
function setTimer() {
   timerInterval = setInterval(() => {
    if (elapsedTime < duration) {
      elapsedTime += 1;
    } else {
      elapsedTime = 0; // Reset when the duration is reached
    }
  }, 1000); // Update every second
  ; // Reset the elapsed time when the timer is
}


function resetTimer() {
elapsedTime = 0;
duration = 10; // Reset duration to default
clearInterval(timerInterval);
}

</script>





<style>
  .progress {
    width: 100%;
    height: 20px;
  } 
</style>




<div>


  <h1 class="text-3xl font-bold mb-4" >Awad Timer</h1>
   
  <div class="container flex  gap-5  items-center justify-center p-6 rounded-md m-5">

    <progress
    class="progress progress-primary w-56"
    value={elapsedTime}
    max={duration}
    ></progress>
  </div>
  <label for="" class="p-2 border rounded">{elapsedTime}</label>
  <label for="">Duration: {duration}</label>
  <input type="range" min="1" max="60" oninput={setTimer} bind:value={duration} class="range range-primary w-56" />

  <button onclick={resetTimer} class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Reset</button>
</div>


 -->
