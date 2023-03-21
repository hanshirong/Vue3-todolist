<template>
    <ToDoList msg="todoList"/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ToDoList from '@/components/ToDoList.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'HomeView',
  components: {
    ToDoList,
  },
});
</script>
