<template>
    <div>
      <button @click="showDialog">打开对话框</button>
      <p>计数: {{ count }}</p>
      <Dialog v-if="dialogVisible"
              @close="closeDialog"
              @confirm="handleConfirm">
        <div>
          <label>输入数字:</label>
          <input type="number" v-model="inputValue">
        </div>
        <div>两倍: {{ inputValue * 2 }}</div>
        <div>
          <button @click="clearInput">清空</button>
          <button @click="handleConfirm">确认</button>
        </div>
      </Dialog>
    </div>
  </template>
  
  <script>
  import Dialog from '../components/Dialog.vue';
  
  export default {
    components: {
      Dialog,
    },
    data() {
      return {
        count: 0,
        dialogVisible: false,
        inputValue: '',
      };
    },
    methods: {
      showDialog() {
        this.dialogVisible = true;
      },
      closeDialog() {
        this.dialogVisible = false;
      },
      clearInput() {
        this.inputValue = '';
      },
      handleConfirm() {
        const num = parseInt(this.inputValue);
        if (!isNaN(num)) {
          this.count += num;
          this.inputValue = '';
          this.dialogVisible = false;
        }
      },
    },
  };
  </script>
  