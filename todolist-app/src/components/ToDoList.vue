<template>
  <h1>{{ msg }}</h1>

  <ul class="ToDoList">
    <li v-for="(item,index) in items" :key="item.id">
        <span v-text="item.title"></span>
        <button v-on:click="deleteItem(item.id)">完成</button>
    </li>
  </ul>

</template>

<script lang="ts">
import { defineComponent,ref,reactive } from 'vue';

export default defineComponent({
  name: 'ToDoList',
  props: {
    msg: String,
  },
  setup(){
    const items = reactive([
      {
        id:1,
        title:"吃"
      },
      {
        id:2,
        title:"睡"
      },
      {
        id:3,
        title:"学习"
      },
    ])

    let deleteItem = (id:number) => {
      // 根据id删除item
      items.forEach((item,index) =>{
        if(item.id == id){
          items.splice(index,1)
        }
      })
      console.log(items)
    }
    
    return{
      items,
      deleteItem
    }

  }
});
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
  /* display: inline-block; */
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
