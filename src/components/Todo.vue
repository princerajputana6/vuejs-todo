<template>
  <div class="Todos">
    <h3>{{ msg }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: bold;
  color: rgb(0, 0, 0);
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
body {
  background: rgb(128, 91, 43);
}
</style>
