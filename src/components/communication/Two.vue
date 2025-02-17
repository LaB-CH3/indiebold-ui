
<template>

    <!-- chat box -->
     <div class="flex flex-col flex-1 h-full bg-white shadow max-w-xl rounded-2xl m-auto">

        <!-- Header -->
        <div class="flex items-center px-3 py-1.5 border-b border-gray-200">
           <div class="size-11 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
             <img src="https://images.pexels.com/photos/1987301/pexels-photo-1987301.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" class="w-full h-full object-cover" />
          </div>
          <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
            <h3 class="text-md font-medium truncate">
                <span>Sarah Williams</span>
                <span class="inline-flex ml-1 bg-green-100 border border-green-500 text-green-600 text-xs px-1 rounded-full">online</span>
            </h3>
            <p class="text-sm truncate font-light">@sarahwillie</p>
          </div>
          <div class="flex gap-3">
            <a href="#" class="size-8 flex items-center justify-center rounded-xl hover:bg-gray-100" v-for="btn in headerBtn">
                <i class="text-xl" :class="btn"></i>
            </a>
          </div>
        </div>

        <!-- Messages -->
        <div class="mx-auto p-4  overflow-y-auto">
         <div v-for="(message, index) in messages" :key="index" class="flex gap-2 mb-8 max-w-[80%]" :class="{'ml-auto justify-end': message.userId == loggedInUser}">
            <div class="size-8 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0" v-if="message.userId != loggedInUser">
               <img :src="findContact(message.userId).avatar" class="w-full h-full object-cover" />
            </div>
            <div class="flex flex-col gap-1">
                <div class="flex">
                    <h3 class="flex-1 text-sm">{{  message.userId == loggedInUser ? 'You' : findContact(message.userId).name }}</h3>
                    <h3 class="text-sm text-gray-600"> {{ message.date }} </h3>
                </div>
                <div :class="['p-3 py-2 text-md font-light rounded-xl', message.userId === loggedInUser ? 'bg-blue-600 text-white' : 'bg-gray-100 text-gray-900']">
                    {{ message.msg }}
                </div>
            </div>
         </div>
       </div>

       <!-- Form -->
       <div class="flex flex-1 flex-col p-4 pt-1">
           <form @submit.prevent="handleSubmit" class="flex flex-col flex-1 relative">
            <textarea rows="3" class="w-full p-2 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-gray-50 border-gray-200" placeholder="Send a message" required></textarea>
           
            <div class="flex gap-2 flex-1 absolute bottom-2 left-2">
              <a href="#" class="size-6 flex items-center justify-center rounded-md hover:bg-gray-200" v-for="btn in editButtons"> <i :class="btn"></i>  </a>
            </div>
        
             <div class="flex items-center gap-2 absolute right-3 bottom-2">
                <a href="#" class="size-6 flex items-center justify-center rounded-md hover:bg-gray-200"><i class="ri-emotion-happy-line"></i></a>
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white cursor-pointer hover:bg-blue-700" type="submit">Send</button>
             </div>
           </form>
         </div>
     </div>


</template>


<script setup>
import { contacts } from '@/utils'    

const loggedInUser = 0
const editButtons = ['ri-attachment-line', 'ri-mic-line']
const headerBtn = ['ri-video-on-line', 'ri-phone-line', 'ri-wallet-line', 'ri-more-2-line']




const findContact = (id) => contacts.find((el) => el.id == id) 
const handleSubmit = () => {

}

const messages = [
{ 
    msg: 'I will let Krystal know',
    userId: 0,
    date: '9:28 AM',
    },
    { 
    msg: 'Here is the latest spec doc we reviewed with the engineers this morning',
    userId: 6,
    date: '9:28 AM',
    },
    { 
    msg: `We haven't had a break in awhile`,
    userId: 6,
    date: '9:28 AM',
    },
    { 
    msg: `Yeah, we haven't gotten lunch together in a ahile either`,
    userId: 0,
    date: '9:28 AM',
    },
    { 
    msg: `We should go back to ramen place. I've been craving it the last few days`,
    userId: 6,
    date: '9:28 AM',
    },
]
</script>