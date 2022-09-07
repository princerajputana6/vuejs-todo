<template>
  <div>
    <h3>Our Tasks</h3>
    <div class="legend">
      <span> <span class="incomplete-box"></span> = Incomplete </span>
      <span> <span class="complete-box"></span> = Complete </span>
    </div>
    <div class="todos">
      <div
        @dblclick="onDblClick(todo)"
        :key="todo.id"
        v-for="todo in allTodos"
        class="todo"
        v-bind:class="{ 'is-complete': todo.completed }"
      >
        {{ todo.title }}
        <i class="fas fa-trash-alt" v-on:click="deleteTodo(todo.id)"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'Todos',
  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
    onDblClick(todo) {
      const updatedTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed,
      };
      this.updateTodo(updatedTodo);
    },
  },
  computed: mapGetters(['allTodos']),
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  grid-gap: 1rem;
  margin: 20px 15px;
}
.todo {
  border: 1px solid #ccc;
  background: #ebebeb;
  padding: 1rem;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  color: rgb(26, 26, 26);
}
i {
  bottom: 10px;
  right: 10px;
  color: rgb(255, 0, 0);
  cursor: pointer;
}
.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box,
.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
}
.complete-box {
  background: #35495e;
}
.incomplete-box {
  background: #ebebeb;
}
.is-complete {
  color: #fff;
  background: #35495e;
}
@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
