<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" id="checkbox" v-on:change="markComplete" />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: #ecf0f1;
  padding: 10px;
  border-bottom: 1px #95a5a6 solid;
}

.todo-item:hover {
  background: #353b48;
  color: #ecf0f1;
}

.is-complete {
  text-decoration: line-through;
  background: #2ecc71;
}

.del {
  background: #e74c3c;
  border: 0ch;
  color: #fff;
  padding: 5px 9px;
  border-radius: 25%;
  cursor: pointer;
  float: right;
  font-size: 1.5vh;
}

.del:hover {
  background: #c23616;
}
</style>