<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="todo.done"
        @change="handleCheck(todo.id)"
      />
      <!-- 如下代码也可以实现，但是不推荐，因为修改了props -->
      <!-- <input type="checkbox" v-model="todo.done" /> -->
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
  </li>
</template>

<script>
import pubsub from "pubsub-js";
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    handleCheck(todoId) {
      this.$bus.$emit("checkTodo", todoId);
    },
    handleDelete(todoId) {
      if (confirm("真的要删除此事件吗？(OAO)!")) {
        // // 事件总线写法
        // this.$bus.$emit("deleteTodo", todoId);
        // pubsub写法
        pubsub.publish("deleteTodo", todoId);
      }
    },
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover {
  background-color: #ddd;
}

li:hover button {
  display: block;
}
</style>