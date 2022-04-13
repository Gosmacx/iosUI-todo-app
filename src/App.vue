<template>

  <!-- Alert Compnent  -->
  <alert v-if="showAlert" :close="closeAlert" />
  

  <div class="flex items-center justify-center flex-col w-full h-screen" >

    <!-- Todo Adder Compnent  -->
    <add-todo :todo="add" />

    <!-- Todo List  -->
    <section class="w-[600px] h-[600px] px-3 max-h-max overflow-y-auto rounded bg-white " >
       <todo-item v-for="item in todos" :key="item" :item="item" :removeTodo="removeTodo" />
    </section>

    <success-menu :success="successRemoveTodo" :cancel="cancelMenu" v-if="showEdit" />

  </div>
</template>

<script setup>

import addTodo from './components/addTodo.vue'
import successMenu from './components/successMenu.vue'
import alert from './components/alert.vue'
import todoItem from './components/todoItem.vue'
import { ref } from 'vue'

const todos = ref([])
const showAlert = ref(false)
const showEdit = ref(false)
const targetTodo = ref(null)

const closeAlert = () => showAlert.value = false;
const cancelMenu = () => showEdit.value = false;

const removeTodo = (todo) => {
  targetTodo.value = todo;
  showEdit.value = true;
}

const successRemoveTodo = () => {
  todos.value = todos.value.filter(item => item !== targetTodo.value)
  targetTodo.value = null
  showEdit.value = false
}

const add = (todo) => {
  if (!todo) return showAlert.value = true  
  todos.value.unshift({
    checked: false,
    text: todo
  })
}

</script>

<style>


.opacitiyEffect{
  animation: fadeIn 0.1s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.form-switch {
  display: inline-block;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}
.form-switch i {
  position: relative;
  display: inline-block;
  width: 46px;
  height: 26px;
  background-color: #e6e6e6;
  border-radius: 23px;
  vertical-align: text-bottom;
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 300ms;
}
.form-switch i::before {
  content: "";
  position: absolute;
  left: 0;
  width: 42px;
  height: 22px;
  background-color: #fff;
  border-radius: 11px;
  transform: translate3d(2px, 2px, 0) scale3d(1, 1, 1);
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 250ms;
}
.form-switch i::after {
  content: "";
  position: absolute;
  left: 0;
  width: 22px;
  height: 22px;
  background-color: #fff;
  border-radius: 11px;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.24);
  transform: translate3d(2px, 2px, 0);
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 200ms;
}
.form-switch:active i::after {
  width: 28px;
  transform: translate3d(2px, 2px, 0);
}
.form-switch:active input:checked + i::after { transform: translate3d(16px, 2px, 0); }
.form-switch input { display: none; }
.form-switch input:checked + i { background-color: #4BD763; }
.form-switch input:checked + i::before { transform: translate3d(18px, 2px, 0) scale3d(0, 0, 0); }
.form-switch input:checked + i::after { transform: translate3d(22px, 2px, 0); }

</style>