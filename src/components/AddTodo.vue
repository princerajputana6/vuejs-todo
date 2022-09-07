<template>
  <div class="main-block">
    <h3>Add Todo</h3>
    <div class="add">
      <form @submit="onSubmit">
        <input type="text" v-model="title" placeholder="Add Todo" />
        <input type="submit" value="Add" />
      </form>
      <FilterTodos />
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
import FilterTodos from './FilterTodos.vue';
export default {
  name: 'AddTodo',
  components: {
    FilterTodos,
  },
  data() {
    return {
      title: '',
    };
  },
  methods: {
    ...mapActions(['addTodo']),
    onSubmit(event) {
      event.preventDefault();
      this.addTodo(this.title);

      this.title = '';
    },
  },
};
</script>

<style scoped>
.main-block {
  margin: 20px 15px;
  padding-bottom: 20px;
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  background: #fff !important;
  width: 470px;
  z-index: 99;
}
.add {
  display: flex;
  width: 100%;
}
form {
  display: flex;
  width: inherit;
}

input[type='text'] {
  flex: 10;
  padding: 10px;
  border: 1px solid #35495e;
  outline: 0;
}

input[type='submit'] {
  flex: 2;
  background: #ebebeb;
  color: rgb(26, 25, 25);
  border: 1px solid #35495e;
  cursor: pointer;
}
</style>
