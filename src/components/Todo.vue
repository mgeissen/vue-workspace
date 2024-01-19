<script setup lang="ts">

import type {TodoData} from "@/components/types";

interface Props {
  todoData: TodoData
}

const props = defineProps<Props>()
const emit = defineEmits(['remove'])

const remove = () => {
  emit("remove", props.todoData)
}

</script>

<template>
  <div class="todo-container">
    <div>
      {{ todoData.name }}
    </div>
    <div>
      <button @click="remove">x</button>
    </div>
  </div>
</template>

<style scoped>
.todo-container {
  border: 1px solid black;
  display: flex;
  flex-direction: row;
  gap: 16px;
}
</style>