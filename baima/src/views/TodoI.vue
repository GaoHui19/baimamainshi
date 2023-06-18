<template>
    <div class="todo-app">
      <h1>Todo List</h1>
      <todo-list></todo-list>
    </div>
  </template>
  
  <script setup>
  // 引用组件
  import TodoList from '../components/TodoList.vue';
  </script>
  
  <style>
  .todo-app {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  </style>
  