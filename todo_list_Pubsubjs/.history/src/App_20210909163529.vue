<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <div class="todo-header">
          <input type="text" placeholder="请输入你的任务名称，按回车键确认" />
        </div>
        <ul class="todo-main">
          <li>
            <label>
              <input type="checkbox" />
              <span>xxxxx</span>
            </label>
            <button class="btn btn-danger" style="display: none">删除</button>
          </li>
          <li>
            <label>
              <input type="checkbox" />
              <span>yyyy</span>
            </label>
            <button class="btn btn-danger" style="display: none">删除</button>
          </li>
        </ul>
        <div class="todo-footer">
          <label>
            <input type="checkbox" />
          </label>
          <span> <span>已完成0</span> / 全部2 </span>
          <button class="btn btn-danger">清除已完成任务</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader";
import TodoList from "./components/TodoList";
import TodoFooter from "./components/TodoFooter";

export default {
  name: "App",
  components: [TodoHeader, TodoList, TodoFooter],
  data() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
