<script lang="ts">
  // نوع الرحلة
  type Options = 'one-way-flight' | 'return-flight';

  // دالة ترجع تاريخ اليوم بصيغة YYYY-MM-DD
  function getDate() {
    const date = new Date();
    const [day, month, year] = [date.getDate(), date.getMonth() + 1, date.getFullYear()];
    return `${year}-${month.toString().padStart(2, '0')}-${day.toString().padStart(2, '0')}`;
  }

  // الحالة الحالية للرحلة (افتراضي One Way)
  let selected = $state<Options>('one-way-flight');

  // القيم بتاعة التواريخ هتبقى Strings عشان تشتغل مع input type="date"
  let StartDate = $state(getDate());
  let returnDate = $state(getDate());

  // دالة الحجز
  function handleSubmit(e: Event) {
    e.preventDefault();
    alert(`Flight booked successfully!
Flight Type: ${selected}
Departure Date: ${StartDate}
${selected === 'return-flight' ? `Return Date: ${returnDate}` : ''}`);
  }


   let isDisabled = $derived(
    (selected === 'one-way-flight' && !StartDate) ||
    (selected === 'return-flight' && (!returnDate || new Date(returnDate) < new Date(StartDate))));

</script>

<form onsubmit={handleSubmit}>
  <div class="container flex gap-5 flex-col items-center justify-center p-6 rounded-md m-5 bg-cyan-800">
    <h1 class="text-3xl font-bold mb-4">Awad Book Flight</h1>

    <!-- اختيار نوع الرحلة -->
    <select class="p-2 border bg-blue-800 rounded" bind:value={selected}>
      <option value="one-way-flight">One Way Flight</option>
      <option value="return-flight">Return Flight</option>
    </select>

    <!-- تاريخ المغادرة -->
    <label class="p-2 border rounded">
      Departure Date
      <input
        type="date"
        bind:value={StartDate}
        min={getDate()}
        required
        class="p-2 border rounded"
      />
    </label>

    <!-- تاريخ العودة -->
    <label class="p-2 border rounded">
      Return Date
      <input
        type="date"
        bind:value={returnDate}
        min={getDate()}
        disabled={selected !== 'return-flight'}
        class="p-2 border rounded"
      />
    </label>

    <!-- زر الحجز -->
    <button
      type="submit"
class={`py-2 px-4 rounded font-bold ${
    isDisabled
      ? 'bg-gray-500 cursor-not-allowed'
      : 'bg-green-500 hover:bg-green-700 text-white'
  }`}      disabled={
        isDisabled
      }
    >
      Book
    </button>
  </div>
</form>














<!-- <script lang="ts">


 type Options = 'one-way-flight' | 'return-flight';




  function getDate() {
    const date = new Date();

    const [day,month,year] = [date.getDate(), date.getMonth() + 1, date.getFullYear()];
    return `${year}-${month.toString().padStart(2, '0')}-${day.toString().padStart(2, '0')}`;
  }


  let selected = $state<Options>('one-way-flight');

 let StartDate = $state(new Date());
 let returnDate = $state(new Date());


    function handleSubmit(e:Event) {
      e.preventDefault();
      alert(`Flight booked successfully! \nFlight Type: ${selected} \nDeparture Date: ${StartDate}`);

    }



</script>





  <form action="" onsubmit={handleSubmit} >

    
    <div class="container flex  gap-5 flex-col items-center justify-center p-6 rounded-md m-5 bg-cyan-800">
      


  <h1 class="text-3xl font-bold mb-4" >Awad Book Flight</h1>

  <select class="p-2 border bg-blue-800 rounded" name="" bind:value={selected} id="">

    <option value="one-way-flight">One Way Flight</option>
    <option value="return-flight">Return Flight</option>
  </select>
  <label for="" class="p-2 border rounded">
    <span>Departure Date</span> 
    <input type="date" bind:value={StartDate} min={getDate()} required class="p-2 border rounded" />  
  </label>

  <label for="" class="p-2 border rounded">Return Date
     <input  
     disabled={selected !== 'return-flight'}
      type="date" bind:value={returnDate} 
      min={getDate()} 
      class="p-2 border rounded">
    </label>

    <button type="submit" disabled= {!StartDate && (selected === 'one-way-flight' )  || (selected ==='return-flight' && returnDate < StartDate)}>
      Book
    </button>


</div>


    </form> -->
