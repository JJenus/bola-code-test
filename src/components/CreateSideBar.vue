<template>
    <div class="SideBar Fixed px-5 py-5">
        <div class="flex justify-between">
            <img src="../assets/Noja360-Logo-transparent.png" alt="logo"/>
            
            <button @click="say('hello')" class="text-gray-800 font-bold py-2 px-5 rounded inline-flex items-center">
                <img src="../assets/Frame 1333.png" alt="menu"/>
            </button>
        </div>
        

        <div class="pt-4 px-1">
            <ul>
                <li class="flex text-base font-medium"><img src="../assets/menu-icon.png" alt="icon-logo" class="pr-3"/>Dashboard</li>
                <li class="flex text-base font-medium"><img src="../assets/users.png" alt="icon-logo" class="pr-3"/>Customer</li>
                <li class="flex text-base font-medium"><img src="../assets/package.png" alt="icon-logo" class="pr-3"/>Product</li>
                <li class="flex text-base font-medium text-blue-600 hover:text-black"><img src="../assets/file-minus1.png" alt="icon-logo" class="pr-3"/>Transaction</li>
                <li class="flex text-base font-medium"><img src="../assets/frame.png" alt="icon-logo" class="pr-3"/>Discount</li>
                <li class="flex text-base font-medium"><img src="../assets/users.png" alt="icon-logo" class="pr-3"/>Customer Group </li>
                <li class="flex text-base font-medium"><img src="../assets/file-minus.png" alt="icon-logo" class="pr-3"/>Invoices </li>
                <li class="flex text-base font-medium"><img src="../assets/frame (1).png" alt="icon-logo" class="pr-3"/>Sales Target</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
data() {
  return {
    count: 0
  }
},

methods: {
  say(message) {
    alert(message)
  }
}
}
</script>

<style>
.SideBar{
    width:20%;
    height:100vh;
    background-color: #F9FAFC;
    color:black;
}

li{
    padding-top: 12px;
    padding-bottom: 12px;
    
}
</style>