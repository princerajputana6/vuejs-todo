<template>
  <div class="todo-item">
    <div class="todo-item-left">
      <input type="checkbox" v-model="completed" @change="doneEdit" />
      <div
        v-if="!editing"
        @dblclick="editTodo"
        class="todo-item-label"
        :class="{ completed: completed }"
      >
        {{ title }}
      </div>
      <input
        v-else
        class="todo-item-edit"
        type="text"
        v-model="title"
        @blur="doneEdit"
        @keyup.enter="doneEdit"
        @keyup.esc="cancelEdit"
        v-focus
      />
    </div>
    <!-- end todo-item-left -->
    <div>
      <i
        class="fa-solid fa-trash"
        style="font-size: 16px; color: red;"
        @click="removeTodo(todo.id)"
      ></i>
    </div>
  </div>
  <!-- end todo-item -->
</template>

<script>
export default {
  name: 'todo-item',
  props: {
    todo: {
      type: Object,
      required: true,
    },
    checkAll: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      id: this.todo.id,
      title: this.todo.title,
      completed: this.todo.completed,
      editing: this.todo.editing,
      beforeEditCache: '',
    };
  },

  watch: {
    checkAll() {
      this.completed = this.checkAll ? true : this.todo.completed;
    },
  },
  directives: {
    focus: {
      inserted: function(el) {
        el.focus();
      },
    },
  },
  methods: {
    removeTodo(id) {
      this.$store.dispatch('deleteTodo', id);
    },
    editTodo() {
      this.beforeEditCache = this.title;
      this.editing = true;
    },
    doneEdit() {
      if (this.title.trim() == '') {
        this.title = this.beforeEditCache;
      }
      this.editing = false;
      this.$store.dispatch('updateTodo', {
        id: this.id,
        title: this.title,
        completed: this.completed,
        editing: this.editing,
      });
    },
    cancelEdit() {
      this.title = this.beforeEditCache;
      this.editing = false;
    },
  },
};
</script>
<style>
.todo-item {
  border: 1px solid rgb(212, 212, 212);
  border-radius: 5px;
  padding: 5px 20px;
}
.todo-item input {
  border: none;
}
</style>
