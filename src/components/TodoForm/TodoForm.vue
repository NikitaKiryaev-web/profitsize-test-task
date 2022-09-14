<template>
  <div class="wrapper">
    <div class="todo-bg"></div>
    <div class="todo-bg2"></div>
    <div class="todo">
      <form @submit="onSubmitHandle" class="todo__form">
        <h1 class="todo__title">Todo list</h1>
        <button type="submit" class="todo__api-btn">Add</button>
      </form>
      <ul class="todo__list">
        <TodoItem
          v-for="todo in todos"
          :key="todo.id"
          :toggle="toggleTodo"
          :todo="todo"
          @toggleTodo="toggleTodo(todo)"
        />
      </ul>
      <div class="todo__overlay"></div>
    </div>
  </div>
  <p class="author">© 2022. Kiryaev Nikita</p>
</template>

<script setup lang="ts">
import { ref } from "vue";
import TodoItem from "../TodoItem/TodoItem.vue";
import axios from "axios";
import type { Todo } from "@/models/Todo";

const todos = ref<Todo[]>([]);

async function onSubmitHandle(e: Event) {
  e.preventDefault();
  const res = await axios.get("https://jsonplaceholder.typicode.com/todos");
  todos.value = res.data;
}

function toggleTodo(todo: Todo): void {
  todo.completed = !todo.completed;
}
</script>

<style lang="scss" scoped>
@import "./TodoForm.scss";
</style>
