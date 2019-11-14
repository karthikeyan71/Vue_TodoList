<template>
  <div>
    <h1> Todos </h1>

    <input @keyup="searchString" type="text" placeholder="search" />
    <br/>
    <br/>

    <div @click="$emit('showAdd')" class="submit-button"> Add todo item </div>
    <br />

    <div  v-bind:key="todo.id" v-for="todo in todos">
      <TodoListItem v-bind:todo='todo' v-on:deleteTodo="$emit('deleteTodo', todo.id)"/>
    </div>

  </div>
</template>

<script>

import TodoListItem from './TodoListItem.vue';

export default {
  name: 'Todo',
  props: ['todos'],
  components: {
    TodoListItem
  },
  methods: {
    searchString({target: { value }}) {
      this.$emit('searchString', value);
    }
  }
}

</script>


<style scoped>

input {
  width: 90%;
  padding: 10px 10px;
  border-radius: 10px;
  border: 1px solid grey;
  outline: none !important;
}

.submit-button {
  padding: 5px 10px;
  border-radius: 10px;
  color: #fff;
  box-sizing: border-box;
  width: 150px;
  text-align: center;
  cursor: pointer;
  background-color: steelblue;
}

</style>
