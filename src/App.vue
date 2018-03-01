<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view></router-view>
    <el-button>默认按钮</el-button>
    <el-button type="primary">主要按钮</el-button>
    <el-button type="text">文字按钮</el-button>
    <input placeholder="input输入框">b</input>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
      return {
        num1: 1
      };
    },
    methods: {
      handleChange(value) {
        console.log(value);
      }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>