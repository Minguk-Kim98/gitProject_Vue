<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList @setItem='setTodo'></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>
<script>
import TodoHeader from "@/components/TodoHeader";
import TodoInput from "@/components/TodoInput";
import TodoList from "@/components/TodoList";
import TodoFooter from "@/components/TodoFooter";
export default {
  components: {
    TodoFooter,
    TodoList,
    TodoInput,
    TodoHeader
  },
  methods: {
    setTodo(key, val) {
      localStorage.setItem(key, val);
        this.$store.state.todoItems.find(item=> item.key == key).val = val;
    },
    readItem() {
      if (!localStorage.length)
        return;
      this.$store.state.todoItems.splice(0, this.$store.state.todoItems.length - 1);
      for (let  i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        if (key == 'loglevel:webpack-dev-server')
          continue;
        this.$store.state.todoItems.push({ key, value:localStorage.getItem(key)});
      }
    }
  },
  created() {
  },
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>