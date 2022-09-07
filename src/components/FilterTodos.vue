<template>
  <div>
    <select v-on:change="filterTodos($event)">
      <option value="all">All</option>
      <option value="5">5</option>
      <option value="10">10</option>
      <option value="20">20</option>
      <option value="50">50</option>
    </select>
  </div>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  name: 'FilterTodos',
  methods: {
    ...mapActions(['filterTodos']),
  },
};
</script>

<style scoped>
select {
  margin-left: 5px;
  flex: 10;
  padding: 10px;
  border: 1px solid #41b883;
  outline: 0;
}
</style>
