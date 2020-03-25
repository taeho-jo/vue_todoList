<template>
  <div>
    <TodoHeader />
    <TodoInput v-on:addTodo="addTodo" />
    <TodoList v-bind:propsData="todoItems" v-on:removeTodo="removeTodo" />
    <TodoFooter v-on:removeAll="clearAll" />
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader";
import TodoInput from "./components/TodoInput";
import TodoList from "./components/TodoList";
import TodoFooter from "./components/TodoFooter";

export default {
  data() {
    return {
      todoItems: []
    };
  },
  methods: {
    addTodo(data) {
      localStorage.setItem(data, data);
      this.todoItems.push(data);
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(data, index) {
      localStorage.removeItem(data);
      this.todoItems.splice(index, 1);
    }
  },
  created() {
    if (localStorage.length > 0) {
      for (let i = 1; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
        console.log(localStorage.key(i));
      }
    }
  },
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-align: center;
  background: #f6f6f8;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgb(0, 0, 0, 0.03);
}
</style>
