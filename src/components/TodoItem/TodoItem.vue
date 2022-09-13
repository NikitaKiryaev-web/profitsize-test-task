<template>
  <div class="todo__list-item-wrapper">
    <li
      class="todo__list-item"
      :class="{ 'todo__list-item_done': todo.completed }"
      @click="$emit('toggleTodo')"
    >
      {{ props.todo.title }}
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
