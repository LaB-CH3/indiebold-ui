<template>
        <div class="card flex flex-col w-auto rounded-2xl bg-white shadow max-w-[300px] m-auto">
          <div class="flex items-center p-3 rounded-md overflow-hidden">
          <div class="size-11 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
             <img src="https://images.pexels.com/photos/1987301/pexels-photo-1987301.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" class="w-full h-full object-cover" />
          </div>
          <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
            <h3 class="text-md font-medium truncate">Sarah Williams</h3>
            <p class="text-sm truncate font-light">sarah@indiebold.com</p>
          </div>
          <div class="flex bg-green-100 text-green-500 text-xs font-bold px-2 py-1 rounded-full">PRO</div>
        </div>

        <div class="menu-separator"></div>

        <ul class="flex flex-col pb-2">
         <li v-for="link in links">
            <a href="#" class="text-gray-800 flex gap-2 items-center p-1.5 px-4 hover:bg-gray-100">
            <i class="text-xl" :class="link.icon"></i>
               <span class="text-md font-normal">{{ link.name }}</span>
            </a>
            <div class="flex flex-col" v-if="link?.template">
             <div class="menu-separator"></div>

              <div class="flex py-2 px-5 items-center">
                <div class="flex flex-col flex-1">
                    <h4 class="text-md">Starter Plan</h4>
                    <p class="text-sm text-gray-500">100 sends per month</p>
                </div>
                <div><a href="#" class="border border-gray-200 bg-white  flex p-1 px-3 rounded-lg text-md hover:bg-gray-100 transition-all">Upgrade</a></div>
            </div>
               <div class="menu-separator"></div>
            </div>
        </li>
      </ul>
   </div>
</template>


<script setup>
import { ref } from 'vue'

const links = ref([
    { name: 'Activity', path: '/about', icon: 'ri-pulse-line' },
    { name: 'Bookmarks', path: '/about', icon: 'ri-bookmark-line' },
    { name: 'Settings', path: '/about', icon: 'ri-settings-line', template: true },
    { name: 'Log out', path: '/about', icon: 'ri-logout-circle-r-line' },
])


</script>