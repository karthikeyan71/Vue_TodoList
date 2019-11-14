<template>
  <div id="app">
    <h4> Here are the Todo's </h4>
    <Todo v-bind:todos='filteredList' v-on:searchString='updateSearchString' v-on:showAdd='toggleCreateWindow' v-on:deleteTodo='deleteTodo' />
    <br />
    <NewTodo v-if="createFlag" v-on:addNewTodoItem='addNewTodo' v-on:closeAdd='toggleCreateWindow'/>
    <br />
  </div>
</template>

<script>

import Todo from './components/Todo.vue';
import NewTodo from './components/NewTodo.vue';

export default {
  name: 'app',
  components: {
    Todo,
    NewTodo
  },
  data() {
    return {
      createFlag: false,
      searchString: '',
      todos: [
        {
          id: 1,
          name: 'Task 1',
          startDate: '12/11/2019',
          tag: 'red',
          completed: false,
          description: 'Task talks about the resource allocation for the particular project'
        },
        {
          id: 2,
          name: 'Task 2',
          startDate: '07/11/2019',
          tag: 'green',
          completed: false,
          description: 'Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project.'
        },
        {
          id: 3,
          name: 'Task 3',
          startDate: '12/04/2009',
          tag: 'blue',
          completed: false,
          description: 'Creating new project fro teh finace and the sales department'
        },
        {
          id: 4,
          name: 'Task 4',
          startDate: '12/01/2013',
          tag: 'purple',
          completed: false,
          description: 'Preparing final check list'
        }
      ],
      filteredList: [
        {
          id: 1,
          name: 'Task 1',
          startDate: '12/11/2019',
          tag: 'red',
          completed: false,
          description: 'Task talks about the resource allocation for the particular project'
        },
        {
          id: 2,
          name: 'Task 2',
          startDate: '07/11/2019',
          tag: 'green',
          completed: false,
          description: 'Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project. Analyzing the risk factor in teh taken project and esetimating the resource for the project.'
        },
        {
          id: 3,
          name: 'Task 3',
          startDate: '12/04/2009',
          tag: 'blue',
          completed: false,
          description: 'Creating new project fro teh finace and the sales department'
        },
        {
          id: 4,
          name: 'Task 4',
          startDate: '12/01/2013',
          tag: 'purple',
          completed: false,
          description: 'Preparing final check list'
        }
      ]
    };
  },
  methods: {
    addNewTodo(newData) {
      this.todos = [ ...this.todos, newData ];
      this.filterTodos();
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(({id}) => id !== todoId );
      this.filterTodos();
    },
    toggleCreateWindow() {
      this.createFlag = !this.createFlag;
    },
    updateSearchString(searchString) {
      this.searchString = searchString;
      this.filterTodos();
    },
    filterTodos() {
      this.filteredList = this.todos.filter(({name}) => name.toLowerCase().includes(this.searchString.toLowerCase()));
    }
  }
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }

  body {
      margin: 0 20%;
  }

</style>
