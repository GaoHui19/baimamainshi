<!-- 子组件 Child.vue： -->
<template>
  <div>
    {{ msg }}
  </div>
</template>

<script>
export default {
  props: ['msg'],
  data() {
    return {};
  },
};
</script>

<style scoped></style>
