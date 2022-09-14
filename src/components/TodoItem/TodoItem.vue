<template>
  <div class="todo__list-item-wrapper" @click="$emit('toggleTodo')">
    <li
      class="todo__list-item"
      :class="{ 'todo__list-item_done': todo.completed }"
    >
      <button
        class="todo__list-item-btn"
        :class="{ active: todo.completed }"
      ></button>
      <div class="todo__list-item-text-wrapper">
        {{ props.todo.title }}
        <p class="todo__list-item-text">
          laboriosam mollitia et enim quasi adipisci quia provident illum
        </p>
      </div>
    </li>
  </div>
</template>

<script setup lang="ts">
import type { Todo } from "@/models/Todo";

interface Props {
  todo: Todo;
}

const props = defineProps<Props>();
</script>

<style lang="scss" scoped>
@import "./TodoItem.scss";
</style>
