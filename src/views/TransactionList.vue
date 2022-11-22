<template> 
   <div class="flex Content-section ">
    <SideBar/>

    <div class="m-10">
      <div>
        <h2 class="text-2xl font-bold pb-6">Transaction(56)</h2>
      </div>
      <div class ="container shadow border roundedlg bg-white">
        <div class="action-call flex my-5  ">
          <button class="bg-transparent flex bg-color text-blue-700 font-semibold hover:text-black px-4 mx-4 border border-blue-500 hover:border-transparent rounded items-center">
            <img src="../assets/plus.png" alt="menu" class="px-1"/> Add income
        </button>
        <button class="bg-transparent flex text-red-500 font-semibold hover:text-white py-2 px-4  mx-4 border border-red-500 hover:border-transparent rounded items-center">
          <img src="../assets/plus (1).png" alt="menu" class="px-1"/> Add Expense
      </button>
      <button class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-black py-2 px-4  mx-4 border border-blue-500 hover:border-transparent rounded">
        view debit
      </button>
      <input type="text" placeholder="enter your search here" class="rounded px-6 flex-1 text-gray-100 outline">
      <button class="bg-transparent flex bg-color text-black-500 font-semibold hover:text-black py-2 px-4  mx-4 hover:border-transparent rounded items-center">
        <img src="../assets/ic-filter.png" alt="menu" class="px-1"/>Fitler
      </button>
        </div>
      <table class="table-fixed container">
      <thead>
        <tr class =" py-6 border-t-1 h-10">
          <th class="text-base text-gray-500 font-medium">Date</th>
          <th class="text-base text-gray-500 font-medium">Customer</th>
          <th class="text-base text-gray-500 font-medium">Amount</th>
          <th class="text-base text-gray-500 font-medium">Payment Method</th>
          <th class="text-base text-gray-500 font-medium">Product </th>
          <th class="text-base text-gray-500 font-medium">Quality </th>
        </tr>
        <tr class ="text-base text-black bg-color font-normal py-6 h-10">
          <th class="text-base text-black font-medium">Today</th>
          <th class="text-base text-black font-medium">#75,000</th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody class="text-center text-black">
        <tr class="pb-3 h-10">
          <td class="text-base text-black font-medium">
            <input type="checkbox"  class="pr-3"/>08-Apr-22 <br/>
            <span class="text-xs text-gray-500">8.34pm</span>
          </td>
          <td  class="text-base text-black font-medium">Lukeman Olawale</td>
          <td  class="text-base text-red-500 font-medium">45,000</td>
          <td>Card</td>
          <td></td>
          <td></td>
        </tr>
        <!-- <tr class="pb-3">
          <td>Witchy Woman</td>
          <td>The Eagles</td>
          <td>1972</td>
        </tr>
        <tr class="pb-3">
          <td>Shining Star</td>
          <td>Earth, Wind, and Fire</td>
          <td>1975</td>
        </tr> -->
      </tbody>

    </table>
      
    <div class="pagination flex justify-center items-center h-12 py-3 my-3">
        <a href="#">&laquo; Prev</a>
        <a href="#">1</a>
        <a class="active" href="#">2</a>
        <a href="#">3</a>
        <a href="#">4</a>
        <a href="#">5</a>
        <a href="#">6</a>
        <a href="#"> Next &raquo; </a>
      </div>
      </div>

      <ExpenseModal/>
    </div>
    
  </div>
 
</template>


<script>

import SideBar from '../components/CreateSideBar.vue';
import ExpenseModal from '../components/CreateExpenseForm.vue'
export default {
  components: {
    SideBar,
    ExpenseModal
  }
}

</script>

<style scoped>
 @import url("../style.css");


.Content-section{
  background-color: #F5F6FC ;
} 

.bg-color{
  background-color:#F9F9FF;
}

.pagination a {
  color: black;
  float: left;
  padding: 8px 16px;
  text-decoration: none;
  transition: background-color .3s;
}


.pagination a.active {
  background-color: dodgerblue;
  color: white;
}

.pagination a:hover:not(.active) {background-color: #ddd;}
</style>
