<script setup lang="ts">

import {type Ref, ref} from "vue";
import type {TodoData} from "@/components/types";
import Todo from "@/components/Todo.vue";

const todos: Ref<TodoData[]> = ref([
  {name: "Mattis 1. Todo"},
  {name: "Workation planen"},
]);

const newTodo: Ref<string> = ref("")

const addTodo = () => {
  todos.value.push({name: newTodo.value})
  newTodo.value = "";
}

const removeTodo = (todoData: TodoData) => {
  todos.value = todos.value.filter(todo => todo != todoData)
}

</script>

<template>

  <h1>Todo List</h1>

  <div>
    <input type="text" v-model="newTodo" placeholder="Add you new todo here..." @keyup.enter="addTodo">
    <button @click="addTodo">Todo hinzufügen</button>
  </div>

  <div v-for="todo of todos">
    <Todo :todoData="todo" @remove="removeTodo"></Todo>
  </div>

</template>

<style scoped>

</style>