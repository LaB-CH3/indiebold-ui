<template>

    <div class="grid grid-cols-2 lg:flex bg-white border border-gray-200 rounded-2xl">
        <div class="flex flex-col flex-1 border-r last:border-r-0 border-gray-200 lg:gap-1 p-4" v-for="stat in stats">

            <div class="flex items-center gap-1">
                <i class="text-lg text-gray-500" :class="stat.attr.icon"></i>
                <h3 class="text-sm md:text-md flex-1">{{ stat.label }}</h3>
            </div>

            <div class="flex items-end gap-2">
                <h1 class="text-xl font-medium">{{ stat.value }}</h1>
                <div class="flex items-center gap-1 -translate-y-0.5" :class="{'text-green-500': stat.change.up && stat.change.value != '0', 'text-red-500': !stat.change.up, 'text-gray-500': stat.change.value == '0'}">
                    <svg v-if="stat.change.up" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="size-5">
                      <path fill-rule="evenodd" d="M12.577 4.878a.75.75 0 0 1 .919-.53l4.78 1.281a.75.75 0 0 1 .531.919l-1.281 4.78a.75.75 0 0 1-1.449-.387l.81-3.022a19.407 19.407 0 0 0-5.594 5.203.75.75 0 0 1-1.139.093L7 10.06l-4.72 4.72a.75.75 0 0 1-1.06-1.061l5.25-5.25a.75.75 0 0 1 1.06 0l3.074 3.073a20.923 20.923 0 0 1 5.545-4.931l-3.042-.815a.75.75 0 0 1-.53-.919Z" clip-rule="evenodd" />
                    </svg>
                    <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="size-5">
                       <path fill-rule="evenodd" d="M1.22 5.222a.75.75 0 0 1 1.06 0L7 9.942l3.768-3.769a.75.75 0 0 1 1.113.058 20.908 20.908 0 0 1 3.813 7.254l1.574-2.727a.75.75 0 0 1 1.3.75l-2.475 4.286a.75.75 0 0 1-1.025.275l-4.287-2.475a.75.75 0 0 1 .75-1.3l2.71 1.565a19.422 19.422 0 0 0-3.013-6.024L7.53 11.533a.75.75 0 0 1-1.06 0l-5.25-5.25a.75.75 0 0 1 0-1.06Z" clip-rule="evenodd" />
                    </svg>
                    <span class="text-xs">{{ stat.change.value }}%</span>
                </div>
            </div>

        </div>
    </div>
    </template>
    
    
<script setup>
    
const stats = [
    {  label: 'Total Visits', value: '640', change: { up: false, value: '-14' }, attr: { icon: 'ri-spy-line' }  },
    {  label: 'Views per Visit', value: '1.17', change: { up: false, value: '-3' }, attr: { icon: 'ri-route-line' }  },
    {  label: 'Visit Duration', value: '5m 27s', change: { up: true, value: '6' }, attr: { icon: 'ri-alarm-line' }  },
    {  label: 'Bounce Rate', value: '86%', change: { up: true, value: '0' }, attr: { icon: 'ri-logout-circle-line' }  }
]
    
</script>