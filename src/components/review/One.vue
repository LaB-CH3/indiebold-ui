

<template>
    <form @submit.prevent="handleSubmit" class="mx-auto bg-white rounded-3xl shadow p-6 space-y-6 max-w-lg">
      <!-- Header -->
      <div class="flex items-center gap-4">
        <div class="size-12 border border-gray-200 rounded-full flex items-center justify-center">
          <i class="ri-star-smile-line text-xl"></i>
        </div>
        <div>
          <h2 class="text-md font-medium">Rate Our Product</h2>
          <p class="text-gray-500 text-sm">Provide us with feedback for the product.</p>
        </div>
      </div>
  
      <div class="flex menu-separator"></div>
  
  
      <!-- Rating Stars -->
      <div class="space-y-2">
        <div class="flex items-center gap-1">
          <h3 class="font-medium text-md">Your Rating</h3>
          <i class="ri-information-fill text-gray-300"></i>
        </div>
        <div class="grid grid-cols-5 gap-2">
          <button type="button" v-for="(_, index) in 5"  :key="index" @click="handleStarClick(index)" class="py-2 lg:py-3 rounded-lg border border-gray-200 flex items-center justify-center cursor-pointer transition-all duration-300 hover:bg-gray-50">
            <i class="ri-star-fill text-2xl lg:text-3xl" :class="index < rating ? 'text-orange-400' : 'text-gray-300'"></i>
          </button>
        </div>
      </div>
  
      <!-- Product Name Input -->
      <div class="flex flex-col gap-1">
        <label class="font-medium text-md">Product Name</label>
        <input v-model="productName" type="text" placeholder="Macbook Air M1" class="w-full p-2 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-white border-gray-200" required />
      </div>
  
      <!-- Review Textarea -->
      <div class="space-y-2">
        <div class="flex justify-between">
          <label class="font-medium">Product Review <span class="text-gray-500 font-light">(Optional)</span></label>
          <span class="text-gray-400 font-light text-sm">{{ review.length }}/{{ maxReviewLength }}</span>
        </div>
        <textarea v-model="review" :maxlength="maxReviewLength" rows="4" placeholder="Jot down your thoughts..." class="w-full p-2 border rounded-lg placeholder:font-light focus:ring-4 focus:ring-gray-100 focus:border-black outline-none transition-all duration-200 bg-white border-gray-200"></textarea>
      </div>
  
  
      <!-- Action Buttons -->
      <div class="flex gap-4">
        <button type="button" class="flex-1 px-4 py-2 rounded-lg border border-gray-200 cursor-pointer hover:bg-gray-100 hover:border-gray-100"> Cancel</button>
        <button @click="handleSubmit" type="submit" class="flex-1 px-4 py-2 rounded-lg bg-blue-600 text-white cursor-pointer hover:bg-blue-700">Submit</button>
      </div>
    </form>
  </template>
  
  
  <script setup>
  import { ref } from 'vue'
  
  const rating = ref(0)
  const productName = ref('')
  const review = ref('')
  const maxReviewLength = 200
  
  const handleStarClick = (index) => {
    rating.value = index + 1
  }
  
  const handleSubmit = () => {
    if (!productName.value || !rating.value) return
    
    const formData = {
      rating: rating.value,
      productName: productName.value,
      review: review.value,
      isAnonymous: isAnonymous.value
    }
    
    console.log('Form submitted:', formData)
    // Handle form submission
  }
  </script>