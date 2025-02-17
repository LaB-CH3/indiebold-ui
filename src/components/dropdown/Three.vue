<template>
    <div class="card flex flex-col w-auto rounded-2xl bg-white shadow max-w-[300px] m-auto">

        <div class="flex items-center p-3 rounded-md overflow-hidden relative">
        <div class="size-11 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
            <img src="https://images.pexels.com/photos/1987301/pexels-photo-1987301.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" class="w-full h-full object-cover" />
        </div>
        <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
            <h3 class="text-md font-medium truncate">Sarah Williams</h3>
            <p class="text-sm truncate font-light">Online</p>
        </div>

        <span class="flex size-2 bg-green-500 absolute rounded-full ring ring-white left-12 bottom-5"></span>
        </div>

        <div class="menu-separator"></div>

        <ul class="flex flex-col">
        <li v-for="link in links">
        <span v-if="link.label" class="flex text-sm font-light text-stone-500 ml-4 mb-2">{{ link.label }}</span>

            <a href="#" class="text-gray-800 flex gap-2 items-center p-1.5 px-4 hover:bg-gray-100">
            <i class="text-xl" :class="link.icon"></i>
            <span class="text-md font-normal flex-1">{{ link.name }}</span>
            <span v-if="link.tag" class="text-xs font-light border px-2 py-0.5 rounded-full bg-white">{{ link.tag }}</span>
            <i v-if="link.expand" class="ri-arrow-right-s-line"></i>
            </a>

            <span class="flex menu-separator my-2" v-if="link?.seperator"></span>
        </li>
        </ul>

        <div class="flex flex-col gap-2 p-4">
            <div class="flex">
            <h4 class="flex-1 text-sm">API Calls</h4>
            <h4 class="text-sm font-light">1.2k / 15k</h4>
        </div>
            <div class="flex bg-gray-200 h-2 relative rounded-full overflow-hidden">
            <div class="flex absolute left-0 top-0 h-full w-32 bg-red-500 rounded-full"></div>
            </div>
        <div class="flex text-sm font-light"> Usage resets in 7 days </div>
        </div>
        </div>
</template>



<script setup>
import { ref } from 'vue'

const links = ref([
    { name: 'Profile', path: '/about', icon: 'ri-user-line', label: 'Account', expand: true },
    { name: 'Billing', path: '/about', icon: 'ri-wallet-line', seperator: true, expand: true },
    { name: 'Guides', path: '/about', icon: 'ri-question-line', label: 'Support', tag: '⌘ G' },
    { name: 'Wiki', path: '/about', icon: 'ri-book-open-line', seperator: true, tag: '⌘ W' }
])

</script>