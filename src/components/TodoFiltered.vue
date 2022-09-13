<template>
  <div class="filter-box">
    <div :class="{ active: filter == 'all' }" @click="changeFilter('all')">
      All
    </div>
    <div
      :class="{ active: filter == 'active' }"
      @click="changeFilter('active')"
    >
      Active
    </div>
    <div
      :class="{ active: filter == 'completed' }"
      @click="changeFilter('completed')"
    >
      Completed
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo-filtered',
  computed: {
    filter() {
      return this.$store.state.filter;
    },
  },
  methods: {
    changeFilter(filter) {
      this.$store.dispatch('updateFilter', filter);
    },
  },
};
</script>

<style>
.filter-box {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.filter-box div {
  padding: 5px 10px;
}
</style>
