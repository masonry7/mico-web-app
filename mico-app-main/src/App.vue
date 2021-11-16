<template>
  <div id="app">
    <HelloWorld msg="主应用入口"/>
    <div class="app-box">
      <div id="container-a"></div>
      <div id="container-b">
        <!-- <iframe src="//localhost:8081" frameborder="0"></iframe> -->
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
        entry: '//localhost:9001',
        container: '#container-a',
        activeRule: '/index',
      },
      {
        name: 'vueAppB',
        entry: '//localhost:9002',
        container: '#container-b',
        activeRule: '/index',
      },
          {
        name: 'vueAppC',
        entry: '//localhost:9002/about',
        container: '#container-b',
        activeRule: '/appb',
      },
    ]);
    // 启动 qiankun
    start({ singular: false });
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
