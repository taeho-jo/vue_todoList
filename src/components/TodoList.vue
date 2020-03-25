<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(item, index) in propsData" v-bind:key="item">
        {{ item }}
        <!-- eslint-disable-next-line prettier/prettier -->
        <span class="btn" type="button" @click="removeTodo(item, index)">삭제</span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  props: ["propsData"],
  methods: {
    removeTodo(item, index) {
      this.$emit("removeTodo", item, index);
    }
  }
};
</script>

<style>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0px;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  background: #fff;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  border-radius: 5px;
  position: relative;
}
.btn {
  position: absolute;
  right: 15px;
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-move {
  transition: transform 1s;
}
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
