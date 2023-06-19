<template>
  <div>
    <h2>父级组件</h2>
    <p>从子组件接收到的值: {{ childValue }}</p>
    <input type="text" v-model="inputValue" /> <!-- 输入框绑定inputValue数据 -->
    <button @click="handleClick">向父组件发送值</button> 点击按钮触发handleClick方法
    <Child :child-value="childValue" @child-click="handleChildClick" /> <!-- 将childValue数据传递给子组件，并监听child-click事件 -->
    <span>
      思路逻辑：在父组件中，我们定义了一个inputValue数据，用于绑定输入框的值。当点击按钮时，
      我们将inputValue的值赋给childValue，并将childValue传递给子组件。
      在子组件中，我们通过$emit方法触发了child-click事件，并将一个字符串值作为参数传递给父组件。
    </span>
  </div>
</template>
<script>
import Child from '../components/childVue3.vue';

export default {
  components: {
    Child
  },
  data() {
    return {
      childValue: '',
      inputValue: ''
    };
  },
  methods: {
    handleClick() {
      this.childValue = this.inputValue; // 将inputValue的值赋给childValue
    },
    handleChildClick(value) {
      console.log(value); // 打印子组件传递的值
    }
  }
};
</script>
