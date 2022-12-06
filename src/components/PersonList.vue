<template>
        <ul>
            <li v-for="item in persons" :key="item.id">
                <h2>{{item.name}}</h2>
                <h2>{{item.address}}</h2>
            </li>
        </ul>

        <h1 v-bind:class="{display:show}" > class binding</h1>
        <input v-model="message" />

        <h2>{{message}}</h2>

        <button @click="onClickButton">Child to parent</button>
</template>



<script lang="ts">
import Person from '@/Types/Person'
import { defineComponent, PropType } from 'vue'

export default defineComponent({

props:{
    persons:{
        required:true,
        type:Array as PropType<Person[]>,
    }
},

methods:
{
    onClickButton(){
this.$emit('childClicked','value from child to parent');
    }
},

data()
{
    return{
        show:true,
        message:'test message'
    }
},

    setup() {
        
    },
})
</script>

<style scoped>
  .display{
    background-color: blue;
  }
</style>
