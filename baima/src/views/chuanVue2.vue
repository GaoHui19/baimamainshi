<!-- 父组件 Parent.vue： -->
<template>
  <div>
    <Child :msg="msg"></Child>
    <input v-model="inputValue" />
    <button @click="sendMessage">发送</button>
  </div>
</template>

<script>
import Child from '../components/childVue2.vue';

export default {
  data() {
    return {
      msg: '父组件传给子组件的值',
      inputValue: '',
    };
  },
  components: {
    Child,
  },
  methods: {
    sendMessage() {
      this.msg = this.inputValue;
    },
  },
};
</script>

<style scoped>
</style>

