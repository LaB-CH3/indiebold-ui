<template>
    <div class="bg-white shadow p-6 rounded-3xl max-w-md m-auto">
        <div class="flex flex-col gap-6" v-if="!videoStream">

          <!-- Header -->
          <div class="flex items-center gap-4">
            <div class="size-12 border border-gray-200 rounded-full flex items-center justify-center">
              <i class="ri-camera-line text-xl"></i>
            </div>
            <div>
              <h2 class="text-md font-medium">Take a Photo</h2>
              <p class="text-gray-500 text-sm">Provide us with feedback for the product.</p>
            </div>
          </div>

          <div class="flex menu-separator"></div>

            <p class="text-md">Make sure your camera is connected and your browser allows image capture. When you're ready, click the button below to get started.</p>
            <div class="flex justify-center">
              <button @click="startCamera" class="flex-1 px-4 py-2 rounded-lg bg-blue-600 text-white cursor-pointer hover:bg-blue-700">Start camera</button>
            </div>
        </div>
  
        <div class="started" v-show="videoStream">
          <div class="flex  gap-2" v-if="isCameraActive">
               <div class="flex-1">
                    <button  @click="stopCamera" class="flex gap-2 p-2 rounded-xl cursor-pointer hover:bg-gray-50">
                      <i class="ri-close-large-line"></i> <span>Exit</span>
                   </button>
                </div>
                <button @click="stopCamera" v-if="photos.length > 0" class="flex gap-2 p-2 px-3 cursor-pointer rounded-xl text-green-500 hover:bg-gray-100">
                    <i class="ri-check-line"></i> <span>Use photo</span>
                </button>
                <button @click="capturePhoto" class="border flex gap-2 p-2 px-3 cursor-pointer rounded-xl hover:bg-gray-100 disabled:opacity-50 disabled:cursor-default" :disabled="photos.length > 5">
                    <i class="ri-camera-ai-line"></i> <span>Capture</span>
                </button>
               
            </div>

            <div class="flex flex-col gap-2 mt-4">
                <video ref="camera" autoplay playsinline class="w-full rounded-xl" v-show="isCameraActive"></video>
  
                <div class="grid grid-cols-[repeat(auto-fit,_minmax(120px,_1fr))] gap-3 my-2">
                  <div class="relative" v-for="img in photos">
                    <img :src="img.url" alt="Captured photo" class="w-full rounded-xl"  />
                    <button class="absolute top-0 right-0 size-6 ring ring-white bg-white rounded-full text-red-500 cursor-pointer hover:bg-red-50" @click="removePhoto(img)">
                      <i class="ri-close-circle-line"></i>
                    </button>
                  </div>
                </div>

                <div class="flex menu-separator my-3"></div>

                <div class="flex items-center">
                  <h2 class="flex-1 text-md text-gray-500">{{ photos.length }} photo{{ photos.length > 1 ? 's' : '' }} captured</h2>
                  <button class="border border-gray-200 flex gap-2 p-2 px-4 rounded-xl hover:bg-gray-100" :disabled="photos.length > 5">
                    <i class="ri-download-line"></i> <span>Download All</span>
                  </button>
                </div>
            </div>
  
            <canvas ref="canvas" class="hidden"></canvas>
        </div>
  
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  const emit = defineEmits(['photoCaptured', 'exitCamera'])
  const props = defineProps(['photos'])

  const camera = ref();
  const canvas = ref();
  const capturedImage = ref();
  const isCameraActive = ref(false);
  let videoStream =  null;
  
  
  
  
  const startCamera = async () => {
    try {
      videoStream = await navigator.mediaDevices.getUserMedia({
        video: { facingMode: { ideal: "environment" } }, // Use back camera
      });
  
      if (camera.value) {
        camera.value.srcObject = videoStream;
        isCameraActive.value = true;
      }
    } catch (error) {
      console.error("Error accessing the camera:", error);
      alert("Unable to access the camera. Ensure permissions are granted.");
    }
  };
  
  const capturePhoto = () => {
    if (camera.value && canvas.value) {
      const context = canvas.value.getContext("2d");
      if (context) {
        canvas.value.width = camera.value.videoWidth;
        canvas.value.height = camera.value.videoHeight;
        context.drawImage(camera.value, 0, 0, canvas.value.width, canvas.value.height);
  
        // Convert the canvas content to a data URL
        capturedImage.value = canvas.value.toDataURL("image/png");
  
        props.photos.push({
          url: capturedImage.value,
          date: Date.now()
        })
  
        camera.value.classList.add('animate-scaleDownAndUp');
        setTimeout(() => {
          camera.value?.classList.remove('animate-scaleDownAndUp');
        }, 200);
      }
    }
  };
  
  const stopCamera = () => {
    if (videoStream) {
      videoStream.getTracks().forEach((track) => track.stop());
      videoStream = null;
      isCameraActive.value = false;
    }
  
    emit('exitCamera')
  };
  
  
  
  
  
  const removePhoto = (img) => {
    const index = props.photos.findIndex((photo) => photo.url === img.url);
    if (index !== -1) {
      props.photos.splice(index, 1);
    }
  }
  
  
  </script>
  


<style>

@keyframes scaleDownAndUp {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  30% {
    transform: scale(0.95);
    opacity: 0.8;
  }
  50% {
    opacity: 0.5;
  }
  70% {
    transform: scale(1.05);
    opacity: 0.8;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.animate-scaleDownAndUp {
  animation: scaleDownAndUp 0.5s ease-in-out;
}



</style>
  
  