<template>
  <div id="app">
    <create-todo v-on:add-todo="addTodo"></create-todo>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
  import sweetalert from 'sweetalert';
  import TodoList from './components/TodoList';
  import CreateTodo from './components/CreateTodo';

  export default {
    name: 'app',
    components: {
      TodoList,
      CreateTodo,
    },
    methods: {
      addTodo(newTodo) {
        this.todos.push({
          title: newTodo.title,
          project: newTodo.project,
          done: newTodo.done,
        });
        sweetalert('Success!', 'To-Do created!', 'success');
      },
    },
    data() {
      return {
        todos: [{
          title: 'Todo A',
          project: 'Project A',
          done: false,
        }, {
          title: 'Todo B',
          project: 'Project B',
          done: true,
        }, {
          title: 'Todo C',
          project: 'Project C',
          done: false,
        }, {
          title: 'Todo D',
          project: 'Project D',
          done: false,
        }],
      };
    },
  };
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
