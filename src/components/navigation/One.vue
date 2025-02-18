<template>
    <aside class="w-[280px] h-screen bg-white flex flex-col gap-3 p-2 border border-gray-100">

    <!-- User Tab -->
    <div class="flex items-center p-2 py-1 rounded-xl overflow-hidden cursor-pointer hover:bg-gray-50 transition-all duration-200">
      <div class="size-8 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
        <img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"
          class="w-full h-full object-cover" />
      </div>
        <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
          <h3 class="text-sm font-medium truncate">Sarah Williams <i class="ri-verified-badge-fill text-sky-500"></i></h3>
          <p class="text-xs text-gray-500 truncate font-light">sarah@indiebold.com</p>
        </div>
        <div class="flex bg-red-100 text-red-500 text-xs font-medium px-2.5 py-0.5 rounded-md">Pro </div>
      </div>

      <!-- links -->
      <nav class="flex flex-col flex-1 overflow-y-auto">
        <ul class="flex flex-col flex-1 gap-1">
          <li v-for="link in links">
            <span v-if="link.seperator" class="flex text-sm text-gray-500 font-medium m-3">{{ link.seperator }}</span>

            <a href="#" class="text-gray-800 rounded-full flex gap-3 items-center p-1.5 px-4 hover:bg-gray-100" :class="{'bg-orange-50 text-orange-500': link.name == current }" @click.prevent="current = link.name">
              <i class="text-xl" :class="link.icon"></i>
              <span class="text-md font-normal flex-1">{{ link.name }}</span>
              <span v-if="link.label" class="text-[10px] border p-0.5 px-1 rounded-full bg-white">{{ link.label }}</span>
            </a>
          </li>
        </ul>

        <div class="flex p-4 gap-3 items-center cursor-pointer rounded-md hover:bg-gray-50">
          <i class="ri-mastercard-line text-xl"></i>
          <div class="flex flex-col flex-1">
            <h3 class="text-md">Plan & Billing</h3>
            <p class="text-xs text-gray-500">1,000 actions</p>
          </div>
          <div>
            <div class="text-green-500 bg-green-100 text-xs p-2 py-1 rounded-md">Upgrade</div>
          </div>
        </div>
    </nav>  

</aside>
</template>



<script setup>
import { ref } from 'vue';
const current = ref('Sessions')


const links = ref([
    { name: 'Home', path: '/about', icon: 'ri-home-line' },
    { name: 'Users', path: '/about', icon: 'ri-group-3-line', label: '434' },
    { name: 'Organizations', path: '/about', icon: 'ri-building-line' },
    { name: 'Authentication', path: '/about', icon: 'ri-shield-check-line', seperator: 'Configure' },
    { name: 'Sessions', path: '/about', icon: 'ri-lock-2-line' },
    { name: 'Integrations', path: '/about', icon: 'ri-puzzle-2-line' },
    { name: 'Templates', path: '/about', icon: 'ri-layout-2-line' },
    { name: 'Dark Mode', path: '/about', icon: 'ri-moon-line' },
    { name: 'Webhooks', path: '/about', icon: 'ri-webhook-line' },
    { name: 'API Keys', path: '/about', icon: 'ri-key-2-line', seperator: 'Developer' },
    { name: 'Path', path: '/about', icon: 'ri-link' }
])

</script>