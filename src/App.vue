<!-- js  -->
<script setup>
import { ref } from 'vue';

const inputValue = ref('');
const todoList = ref([
  { text: 'vue', done: 0 },
  { text: 'react', done: 0 },
  { text: 'vercel', done: 0 },
]);

const addTodoListItem = () => {
  todoList.value.push(inputValue.value);
};

const removeTodoListItem = (index) => {
  todoList.value.splice(index, 1);
};

const handleChange = (event) => {
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};
</script>

<!-- html -->
<template>
  <h4>TODO LIST</h4>

  <input v-model="inputValue" />
  <!-- <input :value="inputValue" @change="handleChange" /> -->

  <button @click="addTodoListItem">+</button>

  <div class="todo-item" v-for="(item, index) in todoList">
    <div class="item-list">
      <input type="checkbox" v-model="item.done" />
      <span :class="{ 'done-item': item.done }"> {{ item.text }} </span>
      <button @click="removeTodoListItem(index)">-</button>
    </div>
  </div>
</template>

<!-- css -->
<style scoped>
.item-list {
  display: flex;
  flex-direction: row;
}
.todo-item {
  width: 100%;
  height: 3rem;
  display: flex;
  flex-direction: column;
  border: 1px solid gray;
}
.done-item {
  text-decoration: line-through;
}
</style>
