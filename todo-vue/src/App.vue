<template>
  <div id="app">
    <section class="todoapp">
      <Header @insertTodo="insertTodo"/>
      <Todo
          :todos="filteredList"
            @removeTodo = "removeTodo"
            @updateDone = "updateDone"
            @updateTodo = "updateTodo"/>
      <Footer :filterType = "filterType"
              :size = "filteredList.length"
              @onFilterType = "handleFilterType"/>
    </section>
  </div>
</template>

<script>
import "./assets/css/main.css"

import Header from "@/components/Header";
import Footer from "@/components/Footer";
import Todo from "@/components/Todo";
export default {
  name: 'App',
  components: {
    Todo,
    Footer,
    Header
  },
  data() {
    return {
      todos: [
        {
          id: new Date(),
          text: "Vue 공부",
          isDone: false
        },
        {
          id: new Date() + 1,
          text: "Javascript 공부",
          isDone: false
        }
      ],
      filterType: "All"
    };
  },
  computed: {
    filteredList() {
      switch (this.filterType) {
        case "All": {
          return this.todos
        }
        case "Active": {
          return this.todos.filter((todo) => !todo.isDone)
        }
        case "Completed" : {
          return  this.todos.filter((todo) => todo.isDone)
        }
        default: {
          return []
        }
      }
    }
  },
  methods: {
    insertTodo(text) {
      this.todos = [
          ...this.todos,
        {
          id: new Date().getTime,
          text,
          isDone: false
        }
      ];
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    updateDone(id) {
      const todos = [...this.todos];
      const todo = todos.find(todo => todo.id === id);

      if (todo) {
        todo.isDone = !todo.isDone;
        this.todos = todos;
      }
    },
    updateTodo({ id, text }) {
      const todos = [...this.todos];
      const todo = todos.find(todo => todo.id === id);

      if (todo) {
        todo.text = text;
        this.todos = todos;
      }
    },
    handleFilterType(type) {
      this.filterType = type
    }
  }
};
</script>

<style>
</style>
