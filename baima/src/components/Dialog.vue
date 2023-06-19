<template>
    <div class="dialog-mask">
      <div class="dialog">
        <div class="dialog-header">
          <span class="dialog-title">{{ title }}</span>
          <button class="dialog-close" @click="$emit('close')">X</button>
        </div>
        <div class="dialog-body">
          <slot></slot>
        </div>
        <div class="dialog-footer">
          <slot name="footer"></slot>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        default: '对话框',
      },
    },
  };
  </script>
  
  <style scoped>
  .dialog-mask {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .dialog {
    background-color: #fff;
    border-radius: 20px;
    width: 400px;
    max-width: 100%;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  }
  
  .dialog-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .dialog-title {
    font-size: 18px;
  }
  
  .dialog-close {
    font-size: 14px;
    border: none;
    background-color: transparent;
    cursor: pointer;
  }
  
  .dialog-body {
    padding: 20px;
  }
  
  .dialog-footer {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 10px;
    border-top: 1px solid #ccc;
  }
  
  .dialog-footer button {
    margin-left: 10px;
  }
  </style>
  