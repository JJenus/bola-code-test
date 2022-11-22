<template>
  <div ref="modal" class="bg-white dark:bg-slate-900 hidden rounded-lg px-6 py-8 ring-1 ring-slate-900/5 shadow-xl w-5/12 my-5">
    <form>
    <div>
      <div class="flex justify-between items-center pb-5">
        <h2 class="text-lg font-semibold">New Expenses</h2>
        <img src="../assets/x.png" alt="cancel" @click="closeModal()">
      </div>
      
      <div class="pb-3">
        <label class="block">
          <span class="block text-base font-medium text-slate-700">Amount spent</span>
          <!-- Using form state modifers, the classes can be identical for every input -->
          <input type="numbert" value="Amount"  id="amountSpent" class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
            focus:outline-none focus:border-sky-300 focus:ring-1 focus:ring-sky-300
          "/>
        </label>
      </div>
      <div class="flex w-full justify-between">
        <div class="pb-3 w-5/12 ">
        <label class="block">
          <span class="block text-base font-medium text-slate-700" for="paymentMethod">Payment Method</span>
        
          
          <select id="paymentMethod" class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
            focus:outline-none focus:border-sky-300 focus:ring-1 focus:ring-sky-300">
            <option>Cash</option>
            <option>Debit Card</option>
            <option>Bank transfer</option>
          </select>
        </label>
      </div>
        <div class="pb-3 w-5/12">
        <label for="date"
           class="block text-base font-medium text-slate-700">Date Of Expense</label>
          
          <input t value="Amount" type="date" id="date"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
            focus:outline-none focus:border-sky-300 focus:ring-1 focus:ring-sky-300
          "/>
      </div>
     

      </div>
      <div class="pb-3">
        <label class="block"><span class="block text-base font-medium text-slate-700">What was this payment for? (optional)</span>  </label>
          
          <textarea id="optionalText" placeholder="e.g new purchase of items" class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
            focus:outline-none focus:border-sky-300 focus:ring-1 focus:ring-sky-300"/>
      
      </div>
    </div>

    <div class="h-10 flex justify-between w-full mt-3">
      <div class="w-6/12 flex items-center">
        <input type="checkbox"/>
        <p class="text-sm font-medium pl-3">Create new after submitting</p>
      </div>
      <div class="w-5/12 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded text-center">
        <button class="text-base">Save Expense</button>
      </div>
    </div>
  </form>
  </div>
  
</template>

<script>

export default {
data() {
  return {
    count: 0,
    show: false
  }
},

mounted(){
  console.log('move!');
},

methods: {
    closeModal(){
      let modal = this.$refs.modal;
      modal.classList.add("hidden");
    },

    showModal(){
      let modal = this.$refs.modal;
      modal.classList.remove("hidden");
    }
  }
}
</script>

<style></style>
