<template>
    <section id="addTodo" class="w-[600px] mb-5 rounded h-20 relative bg-white flex items-center justify-center" >
      <a class="text-[#007bff] pl-1 decoration-[#007bff] hover:underline absolute right-2 top-2" href="#" >Clear</a>
      <div class="flex relative items-center justify-center" >
        <input @keyup.enter="addTodo(text)"  v-model="text" type="text" class="w-96 text-gray-600 h-10 rounded-md bg-gray-200 outline-none pl-2" placeholder="Write a Task">
        <button @click="addTodo(text)" class="flex ml-2 rounded-3xl bg-[#007bff] text-white py-1 px-3 items-center justify-center text-sm space-x-1" >
          <span class="font-medium" >Add</span>
        </button>
      </div>
    </section>
</template>

<script setup>
import { ref } from "vue"

const text = ref(null)

const props = defineProps({
    todo: Function
})

const addTodo = (val) => {
    props.todo(val) // call the parent function 
    text.value = null; // reset the input value
}

</script>