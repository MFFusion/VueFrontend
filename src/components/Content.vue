<script setup>
import {ref} from 'vue'
let count = ref(0)
let inputValue= ref('')
let todos = ref([])
function increment() {
  count.value++
  console.log(count)
}
function addTodo(){
  todos.value.push(inputValue.value)
  inputValue.value=''
}
function deleteTodo(todo){
  todos.value = todos.value.filter(t => t !== todo)
}
</script>

<template>
    <div>
      <h1>Counter: {{count}}</h1>
      <div>
        <input type="text" v-model="inputValue"/>
        <button @click="addTodo">Add Todo</button>
        <div class="w-fit mx-2 my-1 px-2 py-1 rounded-md shadow-md bg-blue-500" v-for="todo in todos" :key="todo">
          <h1>{{ todo }}</h1>
          <button class="bg-gray-200 p-2 rounded-md" @click="deleteTodo(todo)" >Delete</button>
          <img :src=" todo " alt="pic"/>
        </div>
      </div>
    </div>
</template>
