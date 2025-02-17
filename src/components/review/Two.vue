<script setup>
import { ref } from 'vue'

const ratings = ref({
  average: 4.7,
  total: '17.4K',
  reviews: 567,
  distribution: [
    { stars: 5, percentage: 45 },
    { stars: 4, percentage: 25 },
    { stars: 3, percentage: 10 },
    { stars: 2, percentage: 15 },
    { stars: 1, percentage: 5 }
  ]
})

const handleWriteReview = () => {
  console.log('Navigate to write review page')
}
</script>

<template>
  <div class="mx-auto bg-white rounded-3xl shadow p-6 space-y-6 max-w-lg">
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

    <!-- Rating Summary -->
    <div class="flex items-center gap-6">
      <div class="text-5xl font-medium">{{ ratings.average.toFixed(1) }}</div>
      <div class="space-y-1">
        <div class="flex gap-1">
          <template v-for="i in 5" :key="i">
            <i  v-if="i <= Math.floor(ratings.average)" class="ri-star-fill text-xl text-orange-400"></i> <!-- Full Star -->
            <i  v-else-if="i === Math.ceil(ratings.average) && ratings.average % 1 >= 0.5" class="ri-star-half-line text-xl text-orange-400"></i> <!-- Half Star -->
            <i v-else  class="ri-star-line text-xl text-gray-200"></i> 
          </template>
        </div>
        <div class="text-gray-600 text-md">
          {{ ratings.average.toFixed(1) }} · {{ ratings.total }} Ratings 
          <a href="#" class="text-gray-600 underline">{{ ratings.reviews }} reviews</a>
        </div>
      </div>
    </div>

    <div class="flex menu-separator"></div>

    <!-- Rating Distribution -->
    <div class="space-y-3">
      <div v-for="rating in ratings.distribution" :key="rating.stars" class="flex items-center gap-3">
        <div class="flex-1 h-4 bg-gray-100 rounded-sm overflow-hidden">
          <div class="h-full bg-orange-400 rounded-sm" :style="{ width: `${rating.percentage}%` }" ></div>
        </div>
        <div class="w-12 text-md text-right">{{ rating.stars }}.0</div>
        <i class="ri-star-fill text-orange-400"></i>
      </div>
    </div>

    <!-- Write Review Button -->
    <button @click="handleWriteReview"  class="w-full mt-4 p-2 rounded-lg border border-gray-200 cursor-pointer hover:bg-gray-100 hover:border-gray-100 flex items-center justify-center gap-2" >
      <i class="ri-pencil-line"></i> Write a Review
    </button>
  </div>
</template>