<script setup>
import { ref } from 'vue';
const photoStore = ref([])

// Navigations
import NavOne from '@/components/navigation/One.vue';
import NavTwo from '@/components/navigation/Two.vue';
import NavThree from '@/components/navigation/Three.vue';

//dropdowns
import UserDWOne from '@/components/dropdown/One.vue';
import UserDWTwo from '@/components/dropdown/Two.vue';
import UserDWThree from '@/components/dropdown/Three.vue';
import UserDWFour from '@/components/dropdown/Four.vue';

//reviews
import RatingOne from '@/components/review/One.vue';
import RatingTwo from '@/components/review/Two.vue';

//stats
import StatOne from '@/components/stats/One.vue';
import StatTwo from '@/components/stats/Two.vue';

//comnnunication
import ChatOne from '@/components/communication/One.vue';
import ChatTwo from '@/components/communication/Two.vue';

//misc
import MiscOne from '@/components/misc/One.vue';
import MiscTwo from '@/components/misc/Two.vue';

//collaboration
import CollabOne from '@/components/collaboration/One.vue';
import CollabTwo from '@/components/collaboration/Two.vue';

</script>

<template>
  <main class="p-5 bg-gray-50">
   
    <!-- demo -->

    <!-- nav -->
    <div class="flex justify-between gap-4">
      <div class="border border-gray-200">
        <NavOne />
      </div>
      <div class="border">
        <NavTwo />
      </div>
      <div class="border border-gray-200">
        <NavThree />
      </div>
    </div>


    <br><br>

    <div class="grid grid-cols-[repeat(auto-fit,_minmax(120px,_1fr))] gap-5">
     <div> <UserDWOne /></div>
     <div> <UserDWTwo /></div>
      <div><UserDWThree /></div>
      <div><UserDWFour /></div>
    </div>

    <br><br>
    <div class="flex justify-center gap-4">
      <div class="w-md"><RatingOne /></div>
      <div class="w-md"><RatingTwo /></div>
    </div>

    <br><br>

    <div class="flex max-w-5xl m-auto h-[600px] rounded-r-3xl overflow-hidden">
     <div class="w-[300px]">
      <ChatOne />
     </div>
     <div class="flex-1">
      <ChatTwo />
     </div>
    </div>

    <br><br>

    <div class="flex gap-4 max-w-5xl m-auto">
      <div class="w-md"><MiscOne :photos="photoStore" /></div>
      <div class="flex-1"><MiscTwo /></div>
    </div>

    <br><br>
    <div class="grid grid-cols-2 gap-5 max-w-5xl m-auto">
      <div><CollabOne /></div>
      <div><CollabTwo /></div>
    </div>

    <br><br>
    <div class="flex flex-col gap-3 max-w-5xl m-auto">
      <StatOne />
      <StatTwo />
    </div>


  </main>
</template>
