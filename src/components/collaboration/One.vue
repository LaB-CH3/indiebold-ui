<template>
    <div class="flex flex-col card rounded-3xl p-5 bg-white gap-4 shadow max-w-lg m-auto">
        <div class="flex items-center gap-3">
            <div class="flex items-center justify-center size-14 border border-gray-200 rounded-full">
                <i class="ri-user-add-line text-xl"></i>
            </div>
            <div class="flex flex-col flex-1">
                <h3 class="text-lg font-medium">Invite to Project</h3>
                <p class="text-md font-light text-gray-500">Collaborate with members on this project.</p>
            </div>
        </div>

        <div class="flex menu-separator"></div>

        <form class="flex flex-col gap-1">
            <label for="">Invite Members</label>
            <div class="flex flex-1 gap-3">
                <div class="flex flex-1 relative">
                  <input placeholder="Email address" class="w-full p-2 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-white border-gray-200" type="email" required />
                
                  <div class="flex items-center absolute right-3 top-1/2 transform -translate-y-1/2">
                    <i class="ri-global-line text-gray-400"></i>
                    <select name="" id="" class=" font-light text-gray-500 focus:outline-none">
                     <option value="view">can view</option> 
                     <option value="edit">can edit</option>
                    </select>
                  </div>
                  
               </div>
               <button class="border border-gray-200 px-4 rounded-lg cursor-pointer hover:bg-gray-100 hover:border-gray-100">Invite</button>
            </div>
          </form>

          <div class="flex flex-col">
            <h3 class="text-md mb-3">Members with access</h3>

            <div v-for="invite in invites" class="flex items-center rounded-md overflow-hidden">
              <div class="size-10 rounded-full overflow-hidden border-gray-300 shrink-0">
                <img :src="invite.avatar" class="w-full h-full object-cover" />
              </div>

              <div class="flex-1 flex flex-col p-2 min-w-0 overflow-hidden transition-all duration-300">
                <h3 class="text-md font-medium truncate">{{ invite.name }}</h3>
                <p class="text-sm truncate text-gray-500 font-light">{{ invite.email }}</p>
              </div>

               <div class="flex items-center">
                <i class="ri-global-line text-gray-400"></i>
                <select name="" id="" class="text-gray-500 font-light focus:outline-none">
                    <option value="view">can view</option> 
                    <option value="edit">can edit</option>
                  </select>
               </div>

            </div>
          </div>

        <div class="flex menu-separator"></div>

        <div class="flex items-center gap-3">
            <div class="flex items-center justify-center size-12 border border-gray-200 rounded-full">
                <i class="ri-link text-xl"></i>
            </div>
            <div class="flex flex-col flex-1">
                <h3 class="text-md font-medium">Members with link</h3>
                <p class="text-sm font-light text-gray-500">Members who have the link have access to this project.</p>
            </div>
        </div>
    </div>
</template>

<script setup>

const invites = [
    {
        name: 'Diana Charles',
        email: 'diana@indiebold.com',
        access: 'view',
        avatar: 'https://images.pexels.com/photos/28890348/pexels-photo-28890348/free-photo-of-stylish-young-woman-with-braided-hair-outdoors.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
    },
    {
        name: 'Fiona George',
        email: 'fiona@indiebold.com',
        access: 'view',
        avatar: 'https://images.pexels.com/photos/1987301/pexels-photo-1987301.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
    },
    {
        name: 'Ethan Lan',
        email: 'julia@indiebold.com',
        access: 'view',
        avatar: 'https://images.pexels.com/photos/2128807/pexels-photo-2128807.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
    },
]


</script>