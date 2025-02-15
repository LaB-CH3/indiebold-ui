<template>
      <div class="card flex flex-col w-auto rounded-2xl bg-white py-2">
      <ul class="flex flex-col">
       <li v-for="link in links">
          <a href="#" class="text-gray-800 flex gap-2 items-center p-1.5 px-4 hover:bg-gray-100">
            <i class="text-xl" :class="link.icon"></i>
            <span class="text-md font-normal">{{ link.name }}</span>
          </a>
          <span class="flex menu-separator my-2" v-if="link.seperator"></span>

          <div class="flex flex-col" v-if="link.template">
            <span class="text-sm ml-4 my-1">Switch account</span>
            <div class="flex flex-col">
                <div class="flex items-center px-4 py-1 rounded-md overflow-hidden cursor-pointer hover:bg-gray-50" v-for="(account, index) in accounts" @click="selected = index">
                    <div class="size-10 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
                       <img :src="account.avatar" class="w-full h-full object-cover" />
                    </div>
                    <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden">
                      <h3 class="text-md font-medium truncate leading-5">{{ account.name }}</h3>
                      <p class="text-sm text-gray-500 truncate font-light">{{ account.email }}</p>
                    </div>
                    <div>
                        <span class="flex items-center justify-center size-4 border border-gray-300 rounded-full" :class="{'border-transparent': index == selected}">
                            <i class="ri-checkbox-circle-fill text-lg text-green-500" v-if="selected == index"></i>
                        </span>
                    </div>
                </div>
            </div>
            <div class="flex p-3">
                <a href="#" class="flex flex-1 items-center justify-center border border-gray-200 p-2 rounded-lg hover:bg-gray-100 hover:border-gray-100">
                    <i class="ri-add-large-line"></i> <span>Add account</span>
                </a>
            </div>
            <span class="flex menu-separator my-2"></span>
          </div>
        </li>
      </ul>
   </div>
</template>




<script setup>
import { ref } from 'vue'

const selected = ref(1)
const links = ref([
    { name: 'View profile', path: '/about', icon: 'ri-user-line' },
    { name: 'Account settings', path: '/about', icon: 'ri-settings-2-line' },
    { name: 'Dark mode', path: '/about', icon: 'ri-moon-line', seperator: true, template: true },

    { name: 'Help center', path: '/about', icon: 'ri-question-line'  },
    { name: 'Log out', path: '/about', icon: 'ri-logout-circle-r-line' }
])

const accounts = ref([
    { 
        name: 'Sienna Hewitt',
        email: 'sienna@indiebold.com',
        avatar: 'https://images.pexels.com/photos/3586798/pexels-photo-3586798.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
    },
    { 
        name: 'Olivia Charles',
        email: 'olivia@indiebold.com',
        avatar: 'https://images.pexels.com/photos/897322/pexels-photo-897322.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
    },
])


</script>