<template>
  <div>
    <h3>子级组件</h3>
    <button @click="handleClick">向父组件发送值</button>
  </div>
</template>

<script>
export default {
  props: {
    childValue: {
      type: String,
      required: true
    }
  },
  methods: {
    handleClick() {
      this.$emit('child-click', '子组件传递的值'); // 触发child-click事件，并传递一个字符串值
    }
  }
};
</script>

<!-- 注释：子组件中定义了一个按钮，当点击按钮时，触发handleClick方法，通过$emit方法向父组件传递一个字符串值 -->

  