<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-for="todo in todos" v-bind:todo="todo" :key="todo.title" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo"></todo>
    </div>
    <!-- <ul>
      <li> Todo A </li> 
      <li> Todo B </li> 
      <li> Todo C </li> 
    </ul>  -->
  </div>
</template>

<script type = "text/javascript" >
  import TodoList from './components/Todo';
  export default {
    props: ['todos'],
    methods: {
      deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
      },
    }
  };
</script>
<style>
</style>