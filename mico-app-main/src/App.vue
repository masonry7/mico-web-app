<template>
  <div id="app">
    <HelloWorld msg="主应用入口"/>
    <div class="app-box">
      <div id="container-a"></div>
      <div id="container-b">
        <iframe src="//localhost:8085" frameborder="0"></iframe>
      </div>
    </div>
    <!-- <iframe src="//localhost:8085" frameborder="0"></iframe> -->
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
        activeRule: '/b',
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
.app-box{
  display: flex;
  justify-content: space-around;
}
#container-a,#container-b{
  background-color: aliceblue;
  width: 400px;
  height: 400px;
}
</style>
