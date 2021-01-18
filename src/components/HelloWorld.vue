<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>The First of many component collections I will be working on.</p>
    <p>All of this is purely WIP and just me tinkering around and breaking stuff. Some components may work from the get-go others may not.</p>
    <p>There is probably a huge difference in each components stylesheet. Sorry about that, but styling isnt the bread and butter this time round.</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>
