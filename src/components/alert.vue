<template>

 <div class="z-10 absolute opacitiyEffect flex items-center justify-center bg-opacity-60 bg-black h-screen w-full" >
    <div id="Alert" class="mt-20 w-96 h-48 rounded-2xl flex-col z-20 flex items-center justify-between bg-gray-200" >
      <div class="grow flex flex-col items-center justify-center" >
        <span class="text-black font-bold text-2xl" >Uyarı</span>
        <span class="text-black font-medium" >Hiç bir şey yazmadın! Bir şeyler yazmalısın</span>
      </div>
      <button @click="close" class="w-full border-t self-end border-t-gray-300 h-12 flex items-center justify-center" >
        <span class="text-[#007bff] font-medium" >OK</span>
      </button>
    </div>
 </div>

</template>

<script setup>

const props = defineProps({
    close: Function
})

</script>