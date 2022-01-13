<template>
  <div class="app-main">
    <h1>Список задач на vue</h1>
    <Form @addTodo="newTask" />
    <ul v-if="todos.length" class="todo-list">
      <todo-item
        v-for="item in todos"
        v-bind:key="item.id"
        v-bind:todo="item"
        @deleteTask="removeTask"
        @doneTask="completeTask"
      />
    </ul>
    <div v-else>
      <h2>Задач нет</h2>
    </div>
  </div>
</template>

<script>
import Form from "./components/Form";
import TodoItem from "./components/TodoItem";

export default {
  emits: ["addTodo", "deleteTask", "doneTsk"],
  data() {
    return {
      todos: [
        { id: 1, text: "Learn js", complete: false },
        { id: 2, text: "Learn vue", complete: false },
        { id: 3, text: "Learn react", complete: false },
      ],
    };
  },
  methods: {
    newTask(todo) {
      this.todos.push({
        id: this.todos.length ? this.todos[this.todos.length - 1].id + 1 : 1,
        complete: false,
        ...todo,
      });
    },
    removeTask(id) {
      this.todos = this.todos.filter((obj) => obj.id !== id);
    },
    completeTask(id) {
      this.todos = this.todos.map((obj) =>
        obj.id === id ? { ...obj, complete: !obj.complete } : obj
      );
    },
  },
  components: {
    Form,
    TodoItem,
  },
};
</script>

<style>
.app-main {
  max-width: 600px;
  margin: 0 auto;
}

.todo-list {
  margin: 0;
  padding: 0;
}
</style>
