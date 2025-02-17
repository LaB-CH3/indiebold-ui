<template>
     <div class="flex flex-col w-auto rounded-2xl bg-white shadow max-w-[300px] m-auto">

        <div class="flex items-center p-3 rounded-md overflow-hidden">
        <div class="size-11 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
            <img src="https://images.pexels.com/photos/1987301/pexels-photo-1987301.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" class="w-full h-full object-cover" />
        </div>
        <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
            <h3 class="text-md font-medium truncate">Sarah Williams</h3>
            <p class="text-sm truncate font-light">sarahwillie@indie.com</p>
        </div>
        <div class="flex bg-red-100 text-red-500 text-xs font-bold px-2 py-1 rounded-full">PRO</div>
        </div>

        <div class="menu-separator"></div>

        <ul class="flex flex-col">
        <li v-for="link in links">
            <a href="#" class="text-gray-800 flex gap-2 items-center p-1.5 px-4 hover:bg-gray-100">
            <i class="text-xl" :class="link.icon"></i>
            <span class="text-md font-normal">{{ link.name }}</span>
            </a>
            <span class="flex menu-separator my-2" v-if="link?.seperator"></span>
        </li>
        </ul>

        <div class="flex p-4 px-5 font-light text-md text-stone-500"> Download the iOS app</div>
        </div>
</template>


<script setup>
import { ref } from 'vue'

const links = ref([
  { name: 'Activity', path: '/about', icon: 'ri-pulse-line' },
  { name: 'Setup', path: '/about', icon: 'ri-send-plane-line' },
  { name: 'Integrations', path: '/about', icon: 'ri-color-filter-line' },
  { name: 'Upgrade', path: '/about', icon: 'ri-star-line', seperator: true },
  { name: 'Dark mode', path: '/about', icon: 'ri-moon-line', seperator: true },
  { name: 'Add account', path: '/about', icon: 'ri-add-large-line' },
  { name: 'Log out', path: '/about', icon: 'ri-logout-circle-r-line' },
])

</script>