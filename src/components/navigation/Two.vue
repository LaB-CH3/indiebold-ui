<template>
      <aside class="bg-[#212126] h-full p-3 flex flex-col gap-3 transition-all duration-300" :class="{'w-[74px]': collapsed, 'w-[280px]': !collapsed}">
   
   <div class="flex items-center gap-3 h-[60px]">
       <div class="flex-1 overflow-hidden whitespace-nowrap transition-all duration-200" :class="{'opacity-0 max-w-0': collapsed, 'opacity-100 max-w-full': !collapsed}">
         <div class="flex flex-1 items-center px-2 rounded-xl overflow-hidden cursor-pointer hover:bg-[#29292f]">
           <!-- Avatar -->
           <div class="size-10 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
             <img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"
               class="w-full h-full object-cover" />
           </div>

           <!-- User Info -->
           <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300"  :class="{'opacity-0 max-w-0': collapsed, 'opacity-100 max-w-full': !collapsed}">
             <h3 class="text-white text-sm font-medium truncate">Sarah Williams <i class="ri-verified-badge-fill text-sky-500"></i></h3>
             <p class="text-gray-400 text-xs truncate">sarah@indie.com</p>
           </div>
         </div>
       </div>
       <div>
         <a href="#" @click.prevent="collapsed = !collapsed">
           <i class="ri-layout-left-line text-xl text-gray-400 hover:text-gray-300 transition-all duration-200"></i>
         </a>
      </div>
   </div>

   <nav class="flex flex-col flex-1 gap-3">
     <!-- Search Bar -->
     <div class="bg-[#161618] relative rounded-xl w-full  transition-all duration-200" :class="{'max-w-auto overflow-hidden cursor-pointer': collapsed, 'max-w-full': !collapsed }" @click="collapsed = false">
       <input type="text" placeholder="Search" class="w-full bg-transparent rounded-xl pl-10 px-4 py-2.5 focus:outline-none focus:ring-2 focus:ring-gray-600 text-gray-400 relative z-10">
       <div class="flex w-full px-3.5 items-center absolute left-0 top-1/2 transform -translate-y-1/2 z-0 text-gray-400">
         <i class="ri-search-2-line text-lg flex-1"></i>
         <span class="text-sm transition-all duration-200" :class="{'opacity-0': collapsed, 'opacity-100': !collapsed}">⌘ F</span>
       </div>
     </div>
     
     <!-- Main Nav Links -->
     <ul class="flex flex-col flex-1 gap-1">
       <li v-for="link in links" :key="link.name">
         <a href="#" class="text-gray-400 flex items-center gap-3 py-2.5 px-3.5  rounded-xl  hover:text-gray-300 transition-all duration-200" :class="{'bg-[#29292f] text-white': link.name === current }"  @click.prevent="current = link.name">
           <i class="text-xl transition-all duration-200" :class="link.icon"></i>
           <span class="text-md font-medium overflow-hidden whitespace-nowrap transition-all duration-200"  :class="{'opacity-0 max-w-0': collapsed, 'opacity-100 max-w-full': !collapsed}">
             {{ link.name }}
           </span>
         </a>
       </li>
     </ul>

     <ul class="flex flex-col gap-1">
       <li v-for="link in linksBottom" :key="link.name">
         <a href="#" class="text-gray-400 flex items-center gap-3 py-2.5 px-3.5  rounded-xl  hover:text-gray-300 transition-all duration-200" :class="{'bg-[#29292f] text-white': link.name === current }"  @click.prevent="current = link.name">
           <i class="text-xl transition-all duration-200" :class="link.icon"></i>
           <span class="text-md font-medium overflow-hidden whitespace-nowrap transition-all duration-200"  :class="{'opacity-0 max-w-0': collapsed, 'opacity-100 max-w-full': !collapsed}">
             {{ link.name }}
           </span>
         </a>
       </li>
     </ul>
   </nav>
 
 </aside>
</template>



  
<script setup>
import { ref } from 'vue'
const current = ref('Inbox')
const collapsed = ref(false)

const links = ref([
  { name: 'Home', path: '/about', icon: 'ri-home-line' },
  { name: 'Tasks', path: '/about', icon: 'ri-list-check-3' },
  { name: 'Inbox', path: '/about', icon: 'ri-notification-line' },
  { name: 'Archive', path: '/about', icon: 'ri-archive-stack-line' },
  { name: 'Reports', path: '/about', icon: 'ri-pie-chart-line' },
  { name: 'Settings', path: '/about', icon: 'ri-settings-2-line' },
])

const linksBottom = ref([
  { name: 'Dark Mode', path: '/about', icon: 'ri-moon-line' },
  { name: 'Log out', path: '/about', icon: 'ri-logout-circle-r-line' },
])

</script>