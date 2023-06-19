<!-- vue3 -->

<template>
    <div>
      <div v-if="!isEditing">{{ value }}</div>
      <input v-else v-model="editValue">
      <button v-if="!isEditing" @click="startEditing">修改</button>
      <button v-else @click="saveValue">保存</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const value = ref('Hello, world!');
  const isEditing = ref(false);
  const editValue = ref('');
  
  function startEditing() {
    isEditing.value = true;
    editValue.value = value.value;
  }
  
  function saveValue() {
    value.value = editValue.value;
    isEditing.value = false;
  }
  </script>
  

  <!-- vue 2 -->
  <!-- <template>
    <div>
      <div v-if="!isEditing">{{ value }}</div>
      <input v-else v-model="editValue">
      <button v-if="!isEditing" @click="startEditing">修改</button>
      <button v-else @click="saveValue">保存</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        value: 'Hello, world!',
        isEditing: false,
        editValue: '',
      };
    },
    methods: {
      startEditing() {
        this.isEditing = true;
        this.editValue = this.value;
      },
      saveValue() {
        this.value = this.editValue;
        this.isEditing = false;
      },
    },
  };
  </script> -->