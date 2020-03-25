<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      v-on:keyup.enter="addTodo"
      placeholder="what do you have to do?"
    />
    <button v-on:click="addTodo">추가</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        let value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      } else {
        alert("내용을 입력하세요");
      }
    },
    clearInput() {
      this.newTodoItem = "";
    }
  }
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: #fff;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
  width: 300px;
}
button {
  border: none;
  background: #2f8b52;
  border-radius: 5px;
  color: #fff;
  padding: 5px;
}
button:focus {
  outline: none;
}
</style>
