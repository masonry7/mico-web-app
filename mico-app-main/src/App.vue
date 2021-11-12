<template>
  <div id="app">
    <HelloWorld msg="主应用入口"/>
    <div id="container-a"></div>
    <!-- <div id="container-b"></div>
    <iframe src="//localhost:8085" frameborder="0"></iframe> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import { registerMicroApps, start } from 'qiankun';


export default {
  name: 'App',
  components: {
    HelloWorld
  },
  mounted(){
    registerMicroApps([
      {
        name: 'vueAppA',
        entry: '//localhost:8083',
        container: '#container-a',
        activeRule: '/',
      },
      {
        name: 'vueAppB',
        entry: '//localhost:8085',
        container: '#container-b',
        activeRule: '/',
      },
     
    ]);
    // 启动 qiankun
    start();
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#container-a,#container-b{
  width: 200px;
  height: 200px;
  overflow: scroll;
}
</style>
