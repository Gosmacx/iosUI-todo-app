<template>
      <div class="w-full h-12 border-b whitespace-nowrap overflow-hidden text-ellipsis flex items-center justify-between border-b-gray-200" >
        
        <!-- Todo Text  -->
        <span v-if="!renameMode" :class="{checkedItem: item.checked} " class="text-gray-700 whitespace-nowrap overflow-hidden text-ellipsis" > 
          {{ item.text }}
        </span>

        <!-- Rename Mode -->
        <input v-model="item.text" v-else  type="text" class="text-white rounded shadow shadow-gray-600 outline-none bg-red-500 p-1 whitespace-nowrap overflow-hidden text-ellipsis" >


        <!-- Edit Button  -->
        <button class="group text-[#007bff] relative pl-1 decoration-[#007bff] hover:underline" href="#" >
          
          <span>Edit</span>

          <!-- Edit Menu  -->
          <div class="w-60 pb-2 opacitiyEffect invisible group-focus-within:visible opacity-0 group-focus-within:opacity-100 transition-all rounded-xl z-10 bg-gray-200 fixed" >
              
            <!-- Items  -->
            <div class="h-12 text-gray-800 flex items-center justify-between px-2 border-b border-b-gray-300" >
               <span>Complete Task</span>
               <label class="form-switch">
                 <input @click="check" :checked="item.checked" type="checkbox"><i></i>
               </label>
             </div>

             <div v-if="!renameMode" @click="renameMode = !renameMode" class="h-12 flex items-center justify-between px-2 border-b border-b-gray-300" >               
               <span class="text-gray-800" >Rename</span>
              <img src="../assets/rename.png" alt="">
            </div>

             <div v-else @click="renameMode = false" class="h-12 flex items-center justify-between px-2 border-b border-b-gray-300" >               
               <span class="text-[#007bff]" >Save</span>
              <img src="../assets/rename.png" alt="">
            </div>

             <div @click="removeTodo(item)" class="h-12 text-red-500 flex items-center justify-between px-2 border-b border-b-gray-300" >               
               <span>Remove</span>
              <img src="../assets/remove.png" alt="">
            </div>

          </div>

        </button>
      </div>
</template>

<script setup>
import { ref } from "vue"

const renameMode = ref(false)

const props = defineProps({
    item: Object,
    removeTodo: Function
})

const check  = () => {
  props.item.checked = !props.item.checked // toggle the checked state
}

</script>

<style scoped>
.checkedItem{
  color: #34c759 !important;
}
</style>