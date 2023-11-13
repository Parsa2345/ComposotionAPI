<template>
  <div class="hello">
    <h1 @click="alertMessage">{{ message }}</h1>
    <h2 @click="inc">{{ count }}</h2>
    <h3  >{{ count2 }}</h3>
    <h3 >{{ formData.name }}</h3>
    <h3  >{{ messages }}</h3>
    <h3  >{{ formData2.value }}</h3>
    <h3  >{{ getCount }}</h3>
 
  </div>
</template>

<script>

import {ref,reactive, toRefs,inject,computed,watch,watchEffect} from 'vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup(props,context) {
    const { msg:message } = toRefs(props);
    console.log(message);  
    const messages=inject("msg2");
    const count = ref(2);
    const count2 = ref(2);
    const getCount = computed(() =>{
      return count.value +101;});
    // const count2 = reactive({ name:"mohsen",_:1});
    const formData=reactive({
      name:"mohsen",
      family:"parsa",
      email:"test@test.com"
    });
    const formData2=reactive({
      value:"mohsen",
      family:"parsa",
      email:"test@test.com"
    });

    
    function alertMessage(){
      alert(messages);
    }

    function inc(){
      // console.log(getCount);
      count.value += 1;
      count2.value  += 1;
      // console.log(count);
      // console.log(count2);
      // console.log(formData);
      formData.name +="ali";
      context.emit("alertName",formData.name);
    }
    watch(count,(currentCount,oldCount)=>{
      console.log(` count: ${count.value}, currentCount: ${currentCount}, oldCount: ${oldCount}`);
    });
    watchEffect(()=>{
      console.log(count.value);
    });


    return{alertMessage,inc,message,count,count2,formData,messages,formData2,getCount};
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
