<template>

  <!-- contacts list -->
  <div class="flex flex-col h-full bg-white card">
     <div class="flex items-center gap-3 p-5">
          <h3 class="flex-1 text-lg font-medium">Messages</h3>
          <a href="#" class="size-8 flex items-center justify-center rounded-full hover:bg-gray-100"> <i class="ri-search-line text-xl"></i> </a>       
     </div>


      <div class="flex flex-col overflow-y-auto">
          <div class="flex items-center px-4 py-1.5 border-t border-gray-200 cursor-pointer hover:bg-gray-50" v-for="contact in contacts" :class="{'bg-blue-50': contact.active}">
           <div class="size-10 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
             <img :src="contact.avatar" class="w-full h-full object-cover" />
          </div>
         <div class="flex-1 flex flex-col p-2 min-w-0 transition-all duration-300">
          <div class="flex items-center">
              <h3 class="text-sm font-medium truncate flex-1">{{ contact.name }}</h3>
              <span class="text-xs text-gray-500 font-light">{{ contact.msg.date }}</span>
          </div>
          <div class="flex gap-2 items-center relative">
              <p class="text-sm truncate font-light flex-1" :class="{'text-gray-500': contact.msg.read}">{{ contact.msg.text }}</p>
              <div class="flex">
                  <i v-if="contact.msg.read" class="ri-check-double-line text-blue-500"></i>
                  <span v-else class="size-4 flex items-center justify-center text-white text-xs rounded-full bg-red-500">4</span>
              </div>
          </div>
        </div>
      </div>
   </div>

</div>

</template>


<script setup>
import { contacts } from '@/utils'    


</script>