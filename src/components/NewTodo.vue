<template>

  <div class="whole-page">
    <h3> Creating new Todo </h3>
    <div class="todo-holder">
      <li>Name</li>
      <li> <textarea v-model='name' placeholder="Task name"></textarea> </li>
      <li>Description</li>
      <li> <textarea v-model='description' placeholder="Task description"></textarea> </li>
      <li>Start Date</li>
      <li> <textarea v-model='startDate' placeholder="Starting on"></textarea> </li>
    </div>
    <br />
    <div class="submit-button" @click="addNewTodoItem"> Add item </div>
    <br />
  </div>

</template>


<script>

  import uuid from 'uuid';

  export default {
    name: 'NewTodo',
    data() {
      return {
        name: '',
        description: '',
        startDate: ''
      }
    },
    methods: {
      addNewTodoItem() {
        const { name, description, startDate } = this;
        const newTodoItem = {
          id: uuid.v4(),
          name,
          description,
          startDate,
          tag: 'red',
          completed: false
        };

        this.$emit('addNewTodoItem', newTodoItem);
        this.$emit('closeAdd');
      }
    }
  }

</script>


<style scoped>

.whole-page {
  position: fixed;
  background: rgba(255,255,255,0.9);
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 20%;
  top:0;
  left:0;
}

.submit-button {
  padding: 5px 10px;
  border-radius: 10px;
  border: 1px solid grey;
  box-sizing: border-box;
  width: 100px;
  text-align: center;
  cursor: pointer;
}

.todo-holder {
  display: flex;
  flex-wrap: wrap;
}

li {
  margin: 5px 0;
  display: block;
  width: 40%;
  list-style: none;
  height: 70px;

}

textarea {
  height: 60px;
  width: 90%;
  resize: none;
}

</style>
