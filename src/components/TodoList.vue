<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-for="todo in todos" v-bind:todo="todo" :key="todo.title" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo"></todo>
    </div>
  </div>
</template>

<script type = "text/javascript" >
  import swal from 'sweetalert';
  import Todo from './Todo';

  export default {
    props: ['todos'],
    components: {
      Todo,
    },
    methods: {
      deleteTodo(todo) {
        swal({
          title: 'Are you sure?',
          text: 'This To-Do will be permanently deleted!',
          icon: 'warning',
          buttons: true,
          dangerMode: true,
        }).then(
          (value) => {
            if (value) {
              const todoIndex = this.todos.indexOf(todo);
              this.todos.splice(todoIndex, 1);
              swal('Deleted!', 'Your To-Do has been deleted.', 'success');
            }
          });
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
        swal('Success!', 'To-Do completed!', 'success');
      },
    },
  };
</script>
<style>
</style>