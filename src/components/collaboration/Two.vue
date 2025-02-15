<template>
    
    <div class="flex flex-col card p-5 gap-6 rounded-3xl bg-white">
        <form @submit.prevent="handleSubmit" class="flex flex-col flex-1 relative bg-gray-100 rounded-xl">
            <textarea rows="5" class="w-full p-2 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-gray-50 border-gray-200" placeholder="Add comment..."></textarea>
        
            <div class="flex items-center w-[96%] p-2 absolute bottom-0 left-2">
                  <div class="flex gap-2 flex-1">
                    <a href="#" class="size-6 flex items-center justify-center rounded-md hover:bg-gray-200" v-for="btn in editButtons">
                        <i :class="btn"></i>
                    </a>
                 </div>
                 <div class="flex items-center gap-2">
                    <a href="#" class="size-6 flex items-center justify-center rounded-md hover:bg-gray-200"><i class="ri-at-line"></i></a>
                    <button class="flex items-center justify-center rounded-full bg-red-500 text-white px-3 py-1 hover:bg-red-500">Send</button>
                  </div>
                </div>
           </form>

           <div class="flex menu-separator"></div>

           <div class="flex">
            <div class="flex items-center gap-2 flex-1">
                <h3 class="text-lg font-medium">Comments</h3>
                <div><span class="flex px-2 text-sm bg-red-500 text-white rounded-full">25</span></div>
             </div>
             <div class="flex items-center">
                <i class="ri-sort-number-desc"></i>
                <select name="" id="" class=" font-light focus:outline-none">
                    <option value="view">Most recent</option> 
                    <option value="edit">Most liked</option>
                </select>
               </div>
           </div>


        <div class="flex flex-col mt-3 gap-6">
            <div class="flex flex-col gap-3 border-b border-gray-200 pb-6" v-for="comment in comments">
                <div class="flex relative gap-3 items-center">
                    <div class="size-9 rounded-full overflow-hidden border-gray-300 cursor-pointer shrink-0">
                       <img :src="comment.user.avatar" class="w-full h-full object-cover" />
                    </div>
                    <h4 class="text-md">{{ comment.user.name }}</h4>
                    <span class="text-gray-500 text-sm">{{ comment.data.date }}</span>

                    <span class="flex size-2 bg-green-500 absolute rounded-full ring ring-white left-8 bottom-1" :class="{ 'bg-gray-500': !comment.user.online  }"></span>
                </div>
                <div class="flex flex-1">
                    <p class="text-sm font-light">{{ comment.data.comment }}</p>
                </div>
                <div class="flex gap-5 items-center">
                    <a href="#" class="flex items-center justify-center gap-1 rounded-md hover:text-red-500 text-gray-500">
                        <i class="ri-thumb-up-fill"></i> <span class="text-sm">{{ comment.data.upvotes }}</span>
                    </a>
                    <a href="#" class="flex items-center justify-center gap-1 rounded-md hover:text-red-500 text-gray-500">
                        <i class="ri-thumb-down-fill"></i> <span class="text-sm">{{ comment.data.downvotes }}</span>
                    </a>
                    <a href="#" class="flex items-center justify-center gap-1 rounded-md hover:text-red-500 text-gray-500">
                        <i class="ri-chat-1-fill"></i> <span class="text-sm">Reply</span>
                    </a>
                </div>
            </div>
        </div>

        <div class="flex justify-center text-center gap-2 text-gray-500 mt-2">
            <i class="ri-loader-line"></i> loading...
        </div>
    </div>
</template>

<script setup>

const comments = [
    { 
        user: {
             name: 'Floyd Miles', 
             avatar: 'https://images.pexels.com/photos/769690/pexels-photo-769690.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
             online: true
        },
        data: {
            comment: `Actually, now that I try out the links on my message, above, none of them take me to the secure site. Only my shortcut on my desktop, which I created months ago`,
            date: '58 minutes ago',
            upvotes: 25, downvotes: 3
        }
    },
    { 
        user: {
             name: 'Albert Flores', 
             avatar: 'https://images.pexels.com/photos/30368413/pexels-photo-30368413/free-photo-of-blonde-woman-outdoors-relaxed-portrait.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
             online: false
        },
        data: {
            comment: `Before installing this plugin please put back again your wordpress and site url to http`,
            date: '5 hours ago',
            upvotes: 2, downvotes: 0
        }
    },
]

const editButtons = ['ri-bold', 'ri-italic', 'ri-underline', 'ri-link']

const handleSubmit = () => {

}

</script>