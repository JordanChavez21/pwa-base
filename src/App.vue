<template>
  <section class="todoapp">
    <header>
      <h1>Treas</h1>
      <input
        type="text"
        class="new-todo"
        autofocus
        autocomplete="off"
        placeholder="Escribe tu tarea aqui"
        v-model="newTodo"
        @keyup.enter="addTodo()"
      />
    </header>
    <section>
      <ul>
        <li class="todo-list" v-for="todo in todos" :key="todo.id">
          <input class="toggle" type="checkbox" :checked="todo.completed" />
          {{ todo.title }} || {{ todo.completed }}
        </li>
      </ul>
    </section>
  </section>
</template>
<script>
/* eslint-disable */
export default {
  data: () => ({
    todos: [],
    newTodo: "",
  }),
  methods: {
    addTodo() {
      const value = this.newTodo && this.newTodo.trim();

      const todoItem = {
        id: this.todos.length + 1,
        title: value,
        completed: false,
      };

      if (!value) {
        return;
      }

      this.todos.push(todoItem);
    },
  },
};
</script>
<style>
@import "./styles/todomvc-base.css";
@import "./styles/todomvc-index.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
