<!--渲染模版-->
<template>
<div>
  <h1>{{ msg }}</h1>
  <Hello />

</div>

</template>

<!--样式描述-->
<style scoped>
  h1 {
    color: red;
  }
</style>

<!--组件逻辑-->
<script>
import Hello from "./components/Hello.vue";
  export default {
    data() {
      return {
        msg: 'Hello,vue-Webpackdd'
      }
    },
    components: {
      Hello
    }
  }
</script>