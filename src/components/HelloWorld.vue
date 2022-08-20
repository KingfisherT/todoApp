<template>
  <div>
    <h1>{{ msg }}</h1>
    <counter />
    <TodoList />
  </div>
</template>

<script>
import Counter from "./Counter.vue";
import TodoList from "./TodoList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    Counter,
    TodoList,
  },
};
</script>
