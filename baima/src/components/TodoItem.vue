
<!-- 完成按钮操作  组件-->

<template>
    <!-- 如果不处于编辑状态，显示任务内容、修改按钮和删除按钮 -->
    <div class="todo-item" v-if="!editing">
      <span>{{ todo.content }}</span>
      <button @click="editTodo">修改</button>
      <button @click="deleteTodo">删除</button>
    </div>
    <!-- 如果处于编辑状态，显示输入框、保存按钮 -->
    <div class="todo-item" v-else>
      <input type="text" v-model="content">
      <button @click="saveTodoEdit">保存</button>
    </div>
  </template>
  
  <script setup>
  import { ref, defineEmits } from 'vue';
  
  // 定义响应式变量
  const editing = ref(false); // 是否处于编辑状态
  const content = ref(props.todo.content); // 输入框中的内容
  
  // 定义自定义事件
  const emit = defineEmits(['delete', 'save-edit']);
  
  // 进入编辑状态
  function editTodo() {
    editing.value = true;
  }
  
  // 删除任务
  function deleteTodo() {
    emit('delete');
  }
  
  // 保存任务编辑
  function saveTodoEdit() {
    if (content.value.trim() !== '') { // 如果输入框中的内容不为空
      emit('save-edit', content.value); // 触发 save-edit 事件，将新的任务内容作为参数传递
      editing.value = false; // 退出编辑状态
    }
  }
  </script>
  
  <style>
  .todo-item {
    border: 1px solid black;
    padding: 20px;
    margin-bottom: 10px;
    width: 300px;
  }
  
  .todo-item input {
    margin-right: 10px;
  }
  </style>
  