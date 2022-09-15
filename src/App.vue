<script setup lang="ts">
import { ref } from 'vue';
import Input from './components/Input.vue';

type Todo = string;

const text = ref('');
const todos = ref<Todo[]>([]);

const setText = (value: Todo) => text.value = value
const addTodo = () => {
  if(!text.value) return
  todos.value = [...todos.value, text.value]
  text.value = ''
}
const removeTodo = (todo: Todo) => todos.value = todos.value.filter((item) => item !== todo)

</script>

<template>
  <main class="home">
    <div class="actions">
      <Input
        class="input"
        placeholder="Digite uma tarefa"
        :value="text"
        @change="setText"
      />
      <button 
        class="button"
        @click="addTodo"
      >
        Adicionar
      </button>
    </div>
    <ul class="list">
      <li 
        v-for="todo in todos"
        class="item"
      >
        <span class="label">{{ todo }}</span>
        <button @click="removeTodo(todo)" class="remove">deletar</button>
      </li>
    </ul>
  </main>
</template>

<style scoped>
.home > .actions {
  margin-bottom: 42px;
}
.home > .actions > .input {
  margin-right: 8px;
}
.home > .actions > .button {
  border-radius: 4px;
}
.home > .list {
  display: flex;
  flex-direction: column;
  gap: 16px;
} 
.home > .list > .item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: var(--color-blue-dark);
  border-radius: 4px;
  padding: 8px;
} 
.home > .list > .item > .remove {
  font-size: 12px;
  background-color: transparent;
  border-radius: 4px;
  transition: 0.5s ease-in-out;
  color: #fff;
}
.home > .list > .item > .remove:hover {
  background-color: #fff;
  color: var(--color-blue-dark);
}
</style>
