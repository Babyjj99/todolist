<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader :addTodo="addTodo"/>
        <MyList :todos="todos" :checkTodo="checkTodo"/>
        <MyFooter />
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader";
import MyList from "./components/MyList";
import MyFooter from "./components/MyFooter.vue";

export default {
  name: "App",
  components: { MyHeader, MyList, MyFooter },
  data() {
    return {
      todos: [
        { id: "001", title: "吃饭", done: true },
        { id: "002", title: "睡觉", done: false },
        { id: "003", title: "打代码", done: true },
      ],
    };
  },
  methods: {
    //添加
    addTodo(todoObj){
      this.todos.unshift(todoObj)
    },
    //勾选
    checkTodo(id){
      this.todos.forEach((todo) => {
        if(todo.id == id) todo.done = !todo.done
      });
    }

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
