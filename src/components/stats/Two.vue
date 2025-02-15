<template>
    <div class="grid grid-cols-2 lg:flex bg-white border border-gray-200 rounded-2xl card">
        <div class="flex flex-col gap-2 flex-1 text-center p-4" v-for="stat in stats">
            
            <h3 class="text-md text-gray-400 font-light">{{ stat.label }}</h3>
            <h1 class="text-3xl font-medium">{{ stat.value }}</h1>

            <div class="flex justify-center items-center gap-1">
                <h4 class="text-md">{{ stat.change.value }}%</h4>
                <i class="ri-arrow-up-line" v-if="stat.change.up"></i>
                <i class="ri-arrow-down-line" v-else></i>
            </div>
        </div>
    </div>
</template>
    
    
<script setup>
const stats = [
    {  label: 'Followers', value: '6,543', change: { up: true, value: '+12' } },
    {  label: 'Likes', value: '24,645', change: { up: false, value: '-8' }  },
    {  label: 'Comments', value: '957', change: { up: true, value: '+12' }  },
    {  label: 'Shares', value: '68,165', change: { up: false, value: '-28' }  }
]
</script>