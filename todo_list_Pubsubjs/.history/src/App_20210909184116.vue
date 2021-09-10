<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <TodoHeader :addNewTodo="addNewTodo" />
        <TodoList
          :todos="todos"
          :checkTodo="checkTodo"
          :deleteTodo="deleteTodo"
        />
        <TodoFooter />
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
  components: { TodoHeader, TodoList, TodoFooter },
  data() {
    return {
      todos: [
        { id: "001", title: "代码", done: true },
        { id: "002", title: "吃饭", done: false },
        { id: "003", title: "睡觉", done: true },
      ],
    };
  },
  methods: {
    // 添加一个todo
    addNewTodo(newTodoObj) {
      this.todos.unshift(newTodoObj);
    },
    // 勾选与取消勾选修改todo的done属性值
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.done = !todo.done;
        }
      });
    },
    // 删除一个todo
    deleteTodo(id) {
      this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
