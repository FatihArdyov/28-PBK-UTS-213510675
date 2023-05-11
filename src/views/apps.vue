<template>
  <div class="todo-app">
    <h1>My Todo List</h1>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="newTodo" placeholder="Add new task">
      <button type="submit">Add</button>
    </form>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.completed">
        <span :class="{ 'completed': todo.completed }">{{ todo.text }}</span>
        <button @click.prevent="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      newTodo: '',
      todos: [
        { text: 'Learn Vue.js', completed: false },
        { text: 'Build a Todo List app', completed: false },
        { text: 'Upload To do list App', completed: false }
      ]
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, completed: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>

body{
  background-color: blanchedalmond;

}
.todo-app {
  max-width: 600px;
  margin: 0 auto;
  font-family: 'Times New Roman', Times, serif;
}

h1 {
  color: rgb(0, 0, 0);
  text-align: center;
}

form {
  display: flex;
  margin-bottom: 20px;
}

form input {
  color: black;
  background-color: olive;
  flex: 1;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 50px;
}

::placeholder{
  color :black;
}

form button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 50px;
  cursor: pointer;
}


ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

li input[type="checkbox"] {
  margin-right: 10px;
}

li span {
  flex: 1;
  font-size: 16px;
}

li .completed {
  text-decoration: line-through;
}

li button {
  margin-left: 10px;
  padding: 5px 10px;
  font-size: 14px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 50px;
  cursor: pointer;
}
</style>