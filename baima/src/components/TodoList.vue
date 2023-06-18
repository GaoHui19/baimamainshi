
<!-- 完成操作逻辑 组件 -->

<template>
  <div class="todo-list">
    <!-- 新建任务表单 -->
    <div class="new-todo">
      <input type="text" v-model="newTodo" placeholder="输入新任务">
      <button @click="addTodo">新建</button>
    </div>
    <!-- 任务列表 -->
    <div class="todo-items">
      <div class="todo-item" v-for="(todo, index) in todos" :key="index">
        <!-- 如果处于编辑状态，显示输入框；否则显示任务内容 -->
        <input type="text" v-if="todo.editing" v-model="todo.content">
        <span v-else>{{ index + 1 }}. {{ todo.content }}</span>
        <!-- 如果不处于编辑状态，显示修改按钮；否则显示保存按钮 -->
        <button v-if="!todo.editing" @click="editTodo(index)">修改</button>
        <button v-else @click="saveTodoEdit(index)">保存</button>
        <button @click="deleteTodo(index)">删除</button>
      </div>
    </div>
    <!-- 提示框 -->
    <div v-if="showAlert" class="alert">
      <p>{{ alertText }}</p>
      <button @click="closeAlert">确定</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// 定义响应式变量
const newTodo = ref(''); // 新建任务表单中的输入框内容
const todos = ref([]); // 任务列表
const showAlert = ref(false); // 是否显示提示框
const alertText = ref(''); // 提示框中的文本内容

// 新建任务
function addTodo() {
  if (newTodo.value.trim() === '') { // 如果输入内容为空
    showAlert.value = true; // 显示提示框
    alertText.value = '输入内容不能为空';
  } else {
    todos.value.push({ // 将新任务添加到任务列表中
      content: newTodo.value,
      editing: false
    });
    newTodo.value = ''; // 清空输入框
  }
}

// 删除任务
function deleteTodo (index) {
  todos.value.splice(index, 1); // 从任务列表中删除指定任务
  for (let i = index; i < todos.value.length; i++) { // 更新任务序号
    todos.value[i].index = i + 1;
  }
}

// 进入编辑状态
function editTodo (index) {
  todos.value[index].editing = true;
}

// 保存任务编辑
function saveTodoEdit (index) {
  const todo = todos.value[index];
  if (todo.content.trim() === '') { // 如果输入内容为空
    showAlert.value = true; // 显示提示框
    alertText.value = '输入内容不能为空';
  } else if (todo.content === todo.originalContent) { // 如果未做出改变
    showAlert.value = true; // 显示提示框
    alertText.value = '并未做出改变';
  } else {
    todo.editing = false; // 退出编辑状态
    todo.originalContent = todo.content; // 更新任务内容
    showAlert.value = true; // 显示提示框
    alertText.value = '保存成功';
  }
}

// 关闭提示框
function closeAlert() {
  showAlert.value = false;
  alertText.value = '';
}
</script>

<style>
.todo-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.new-todo {
  margin-bottom: 10px;
}

.todo-items {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.todo-item {
  border: 1px solid black;
  padding: 20px;
  margin-bottom: 10px;
  width: 300px;
}

.todo-item input {
  margin-right: 10px;
}

.alert {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  border: 1px solid black;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.alert p {
  margin-bottom: 10px;
}
</style>
