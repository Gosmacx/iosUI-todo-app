<template>

 <div class="absolute z-50 opacitiyEffect h-screen w-full bg-black bg-opacity-60 flex items-center justify-center" >
    
    <div class="flex w-[650px] space-y-5 absolute bottom-5 z-20 flex-col items-center justify-between" >
        
        <!-- Top List -->
        <div class="flex px-3 w-full rounded-xl bg-gray-200 flex-col items-center" >
            
            <!-- List Items -->
            <div @click="cancel" class="h-12 cursor-pointer flex items-center justify-center space-x-2 w-full border-b border-b-gray-300" >
                <span class="text-lg font-medium text text-[#007bff]" >Save</span>
            </div>
            <div @click="success" class="h-12 cursor-pointer flex items-center justify-center space-x-2 w-full border-b border-b-gray-300" >
                <span class="text-lg font-medium text-red-500" >Remove</span>
            </div>
            
        </div>
        
        <!-- Bottom Button  -->
        <div @click="cancel" class="w-full h-12 cursor-pointer bg-gray-200 flex items-center rounded-xl justify-center text-[#007bff] " >
            <span class="font-bold text-lg" >Cancel</span>
        </div>

    </div>

 </div>

</template>

<script setup>

const props = defineProps({
    cancel: Function,
    success: Function
})

</script>