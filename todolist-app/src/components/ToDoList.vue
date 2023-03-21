<template>
  <h1>{{ msg }}</h1>
  <div class="inputs">
    代办：<input type="text" v-model="newItem">
    <button v-on:click="addNewItem()">添加</button>
  </div>
  <ul class="ToDoList">
    <li v-for="(item,index) in items" :key="item.id">
        <span v-text="`${item.title}-----${item.id}`"></span>
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
    const newItem = ref()
    let id = 4
    let deleteItem = (id:number) => {
      // 根据id删除item
      items.forEach((item,index) =>{
        if(item.id == id){
          items.splice(index,1)
        }
      })
      console.log(items)
    }

    let addNewItem = () =>{
      if(!newItem.value){
        return
      }
      let obj = {
        // id应该是唯一的，不可以用items.length +1 否则就会出问题
        id:id,
        title:newItem.value
      }
      items.push(obj)
      id++
      newItem.value = ''
    }
    
    return{
      items,
      deleteItem,
      newItem,
      addNewItem
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
