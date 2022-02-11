<script setup>
import { ref } from 'vue';

const items = ref([])

function add() {

  const todoText = document.getElementById('todo-input').value

  console.log(items)
  console.log(items.value)

  items.value.push(todoText)

  document.getElementById('todo-input').value = ''
}

function remove(itemsIndex) {
  console.log('remove')

  items.value.splice(itemsIndex, 1)
}
</script>

<template>
  <div class="todo-list">
    <h1 class="todo-list-h1">Todo List</h1>
    <div class="todo-list-add">
      <input
        type="text"
        id="todo-input"
        placeholder="add Items"
        >
        <button type="button" @click="add()">추가</button>
    </div>
    <div class="todo-items">
      <div v-for="(item, index) in items" :key="index">
        <div>{{ index + 1 }} - {{ item }}</div>
        <button type="button" @click="remove(index)">제거</button>
      </div>
    </div>
  </div>
</template>

<style>
  html, body {
    padding: 0;
    margin: 0;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .todo-list .todo-list-h1 {
    font-size: 24px;
  }

  .todo-list .todo-list-add {
    display: flex;
  }

  .todo-list .todo-items {
    margin-top: 8px;
    display: flex;
    flex-direction: column;
  }

  .todo-list .todo-items > * {
    display: flex;
    justify-content: space-between;
    padding: 4px;
  }
</style>