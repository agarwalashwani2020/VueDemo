<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>

  <button @click="changeName('namteste')">Change Name</button>

  <h5>{{name}}</h5>

  <PersonList :persons="person" @childClicked="ClickEventfired($event)"/>

  <div>{{testMethod}}</div>

  
</template>

<script lang="ts">

import { defineComponent, ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import Person from './Types/Person';
import PersonList from './components/PersonList.vue';

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    PersonList
  },

  data()
  {
    return{
       testName:'abc'
    }
  },
  computed:{
    testMethod()
    {
      return this.testName;
    }
  },
setup(){

  const person=ref<Person[]>([
    {
      id:1,
      name:'name1',
      address:'address1',
      isActive:false
    },
    {
      id:2,
      name:'name2',
      address:'address2',
      isActive:true
    },
  ])
  const name=ref('test1');
  return {name,person};
},
  methods:{
    changeName(name:string)
    {
     
      this.name=name;
    },
      
    ClickEventfired(name: string)
    {
      this.name=name;
    }
      


  }
});
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
