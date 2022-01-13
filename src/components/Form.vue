<template>
  <form class="form">
    <input
      v-model="text"
      class="input"
      type="text"
      placeholder="Введите задачу"
    />
    <input
      v-model="description"
      class="input"
      type="text"
      placeholder="Введите описание задачи"
    />
    <button class="btn" @click.prevent="createNewtask()">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      text: "",
      description: "",
    };
  },

  emits: {
    addTodo: ({ text, description }) => {
      if (text && description) {
        return true;
      } else {
        return false;
      }
    },
  },

  methods: {
    createNewtask() {
      this.$emit("addTodo", {
        text: this.text,
        desc: this.description,
      });
      this.text = "";
      this.description = "";
    },
  },
};
</script>

<style scoped>
.form {
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  margin-bottom: 20px;
}

.input {
  width: 100%;
  padding: 8px 10px;
  margin-bottom: 10px;
}

.btn {
  padding: 5px 10px;
  background-color: transparent;
  border: 1px solid teal;
  cursor: pointer;
}
</style>
