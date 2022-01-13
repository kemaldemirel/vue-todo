<template>
  <li class="todo-item" :class="{ complete: todo.complete }">
    <p>
      {{ todo.text }}
      <br />
      <span>
        {{ todo.desc }}
      </span>
    </p>
    <div class="btn-container">
      <button @click="$emit('doneTask', todo.id)">Готово</button>
      <button @click="$emit('deleteTask', todo.id)">Удалить</button>
    </div>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px 15px;
  border: 1px solid teal;
}

.todo-item.complete {
  background-color: teal;
  color: #fff;
}

.todo-item p {
  font-size: 20px;
  font-weight: 800;
}

.todo-item span {
  font-size: 11px;
  font-weight: 400;
}

.todo-item:not(:last-child) {
  margin-bottom: 20px;
}
</style>
