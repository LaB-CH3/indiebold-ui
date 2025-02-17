<template>
    <div class="flex flex-col p-8 rounded-3xl gap-8 max-w-lg m-auto">
      <div class="flex flex-col text-center">
        <i class="ri-bluesky-fill text-4xl"></i>
        <h1 class="text-2xl font-medium">Create account</h1>
        <p class="text-gray-500 text-sm">Start your 30-day-free trial. Cancel anytime</p>
      </div>

      <div class="flex flex-col gap-3">
        <button v-for="s in socials" :key="s.name" class="flex-1 flex items-center justify-center gap-2 border border-gray-200 shadow p-2 bg-white rounded-xl cursor-pointer hover:bg-stone-100">
          <i :class="s.icon" class="text-xl"></i> <span class="text-md">Connect with {{ s.name }}</span>
        </button>
      </div>

      <div class="flex items-center gap-3 text-gray-500 text-md">
        <span class="flex-1 border-b border-gray-200"></span><span>or sign up with email</span> <span class="flex-1 border-b border-gray-200"></span>
      </div>

      <form action="">
        <div class="flex flex-col gap-5">

          <div class="flex flex-col gap-1">
            <label for="">Email</label>
            <div class="flex relative">
              <input placeholder="hi@indiebold.com" class="w-full p-2 px-10 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-white border-gray-200" type="email" required />
              <i class="ri-mail-line absolute left-4 top-1/2 transform -translate-y-1/2"></i>
            </div>
          </div>

          <div class="flex flex-col gap-1">
            <label for="">Password</label>
            <div class="flex relative">
              <input placeholder="Enter your password" class="w-full p-2 px-10 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-white border-gray-200" :type="showPassword ? 'text' : 'password'" required />
              <i class="ri-lock-line absolute left-4 top-1/2 transform -translate-y-1/2"></i>
              <a href="#" class="absolute right-4 top-1/2 transform -translate-y-1/2" @click.prevent="showPassword = !showPassword">
                <i :class="!showPassword ? 'ri-eye-line' : 'ri-eye-off-line'"></i>
              </a>
            </div>
          </div>

          <div class="flex flex-1">
            <button class="flex-1 px-4 py-2 rounded-lg bg-blue-600 text-white hover:bg-blue-700">Continue</button>
          </div>
          <div class="flex justify-center">
            <p class="text-md font-light">Already have an account? <a href="#" class="text-black border-b">Sign in</a></p>
          </div>
        </div>
      </form>
    </div>
</template>



<script setup>
import { ref } from 'vue'

const showPassword = ref(false)

const socials = ref([
  { name: 'Google', icon: 'ri-google-fill' },
  { name: 'Apple ID', icon: 'ri-apple-fill' },

])

</script>