<template>
  <div class="todo-app">
    <header>
      <h1 class="title">Todo App</h1>
      <form @submit.prevent="createTodo">
        <div class="input-group">
          <input class="todo-input" v-model="todoInput">
          <button type="submit">Add</button>
        </div>
      </form>
    </header>

    <div>
      <TodoItem v-for="(todo, index) in todoList" 
      :todo="todo" 
      :index="index"
      @delete="removeTodo"
       />
    </div>

    <div v-if="todoList.length < 1">
      <h4>Belum ada data</h4>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoItem from '@/components/TodoItem.vue'

const todoInput = ref('')
const todoList = ref([])

const createTodo = () => {
  todoList.value.push(todoInput.value)
  todoInput.value = ''
}

const removeTodo = (index) => {
  todoList.value.splice(index, 1);
}
</script>