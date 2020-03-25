<template>
  <div>
    <span class="allBtn" v-on:click="clearTodos">Clear ALL</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodos() {
      this.$emit("removeAll");
    }
  }
};
</script>

<style>
.allBtn {
  color: red;
  font-weight: 900;
}
</style>
