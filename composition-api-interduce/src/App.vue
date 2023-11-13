<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" @alertName="alertname"  />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import {provide} from 'vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },

  setup(){
    
    function alertMessage(){
      alert("messages");
    }
    function alertname(name){
      alert(name);
    }
provide("msg2","12345");


 return {provide,alertMessage,alertname}
  }
}




</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
