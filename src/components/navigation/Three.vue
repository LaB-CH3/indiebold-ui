<template>
         <aside class="w-[280px] h-full bg-[#f7f7f7] flex flex-col gap-4 p-3">

<div class="flex bg-white border border-gray-200 items-center px-2 rounded-2xl overflow-hidden cursor-pointer transition-all duration-200">
  <div class="size-10 flex items-center justify-center overflow-hidden cursor-pointer shrink-0">
    <i class="ri-bluesky-fill text-4xl"></i>
  </div>
  <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
    <p class="text-sm truncate">Team</p>
    <h3 class="text-md font-medium truncate">Marketing</h3>
  </div>
  <div class="flex">
    <i class="ri-expand-up-down-line"></i>
  </div>
</div>


<!-- Search Bar -->
<div class="relative bg-[#f0f0f0] rounded-xl w-full shadow-inner">
 <input type="text" placeholder="Search" class="bg-transparent w-full rounded-xl pl-10 px-4 py-2.5 placeholder:text-gray-700 relative z-10 border border-gray-200 focus:ring-2 focus:ring-gray-200 focus:border-gray-300 outline-none transition-all duration-200">
 <div class="flex w-full px-3 items-center absolute left-0 top-1/2 transform -translate-y-1/2 z-0">
  <i class="ri-search-2-line text-xl flex-1"></i>
  <span class="text-sm">⌘  F</span>
 </div>
</div>


<nav class="flex flex-col flex-1 overflow-y-auto">
   <!-- Main Nav Links -->
  <ul class="flex flex-col flex-1 gap-2">
    <li v-for="link in links">
      <a href="#" class="border flex gap-2 items-center rounded-xl p-2 px-3 hover:bg-white" 
        :class="{'bg-white border-gray-200  shadow text-[#030404]': isCurrent(link), 'text-gray-600 border-transparent': !isCurrent(link) }" @click.prevent="current = link.name">
        <i class="text-xl" :class="link.icon"></i>
        <span class="text-md font-normal">{{ link.name }}</span>
      </a>
    </li>
  </ul>

  <!-- Bottom links -->
  <ul class="flex flex-col gap-1 border-b-2 border-gray-200 pb-3">
    <li v-for="link in linksBottom">
      <a href="#" class="border flex gap-2 items-center rounded-xl p-2 px-3 hover:bg-white" 
        :class="{'bg-white border-gray-200 shadow text-[#030404]': isCurrent(link), 'text-gray-600 border-transparent': !isCurrent(link) }" @click.prevent="current = link.name">
        <i class="text-xl" :class="link.icon"></i>
        <span class="text-md font-normal">{{ link.name }}</span>
      </a>
    </li>
  </ul>
</nav> 



<div class="flex items-center p-2 rounded-xl overflow-hidden cursor-pointer hover:bg-[#f0f0f0] transition-all duration-200">
   <!-- Avatar -->
    <div class="size-10 rounded-full overflow-hidden cursor-pointer shrink-0">
      <img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"
        class="w-full h-full object-cover" />
    </div>
  <!-- User Info -->
     <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
       <h3 class="text-sm font-medium truncate">Sarah Williams <i class="ri-verified-badge-fill text-sky-500"></i></h3>
       <p class="text-xs truncate font-light">sarah@indie.com</p>
     </div>
     <div class="flex">
       <i class="ri-arrow-right-s-line"></i>
     </div>
   </div>
</aside>
</template>



<script setup>
import { ref } from 'vue'
const current = ref('Inbox')
const isCurrent = (link) => link?.name == current.value

const links = ref([
  { name: 'Home', path: '/about', icon: 'ri-home-fill' },
  { name: 'Discover', path: '/about', icon: 'ri-global-fill' },
  { name: 'Zaps', path: '/about', icon: 'ri-flashlight-fill' },
  { name: 'Inbox', path: '/about', icon: 'ri-inbox-fill' },
  { name: 'Team', path: '/about', icon: 'ri-group-3-fill' },
  { name: 'Apps', path: '/about', icon: 'ri-apps-2-add-fill' },
])


const linksBottom = ref([
  { name: 'Settings', path: '/about', icon: 'ri-settings-2-fill' },
  { name: 'Support', path: '/about', icon: 'ri-headphone-fill' },
])

</script>