<template>
  <div class="todo-list">
    <p> {{todo.name}} <br/>
      Started on : {{todo.startDate}}
      <br/>
      <br/>
      {{todo.description}}
      <br/>
      <br/>
    </p>

    <div class="delete" @click="$emit('deleteTodo', todo.id)"> Delete </div>

    <span v-if="todo.completed">(Task completed)</span>
    <span v-else>(Yet to be completed)</span>

    <div class="bottom-right">
      <input type='checkbox' value="todo.completed" v-on:change="markCompleted"/> <span> (click will reflect in task status) </span>
    </div>

    <div class="ball" v-bind:class="todo.tag"> </div>
    <hr />
    <br />
  </div>
</template>


<script>

  export default {
    name: 'TodoListItem',
    props: ['todo'],
    methods: {
      markCompleted() {
        // console.log('function has ben clicked');
        this.todo.completed = !this.todo.completed;
      }
    }
  }

</script>


<style scoped>

  span {
    font-size:12px;
  }

  .delete {
    padding: 3px 7px;
    background-color: red;
    color: #fff;
    position: absolute;
    top: 10px;
    right: 40px;
    font-size: 12px;
    font-weight: bolder;
    border-radius: 10px;
    cursor: pointer;
  }

  .bottom-right {
    position: absolute;
    bottom: 40px;
    right: 10px;
  }

  .bottom-right input {
    height: 20px;
    width: 20px;
    position: relative;
    top:5px;

  }

  .todo-list {
    position: relative;
  }

  .ball {
    height: 20px;
    width: 20px;
    border-radius: 50%;
    position: absolute;
    right: 10px;
    top: 10px;
  }

  .green {
    background: green;
  }

  .red {
    background: red;
  }

  .blue {
    background: blue;
  }

  .purple {
    background: purple;
  }

</style>
