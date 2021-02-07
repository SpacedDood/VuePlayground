<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>So its no longer the first... It seems I'm going to be using this as a dump for all components I work on.</p>
    <p>All of this is purely WIP and just me tinkering around and breaking stuff. Some components may work from the get-go others may not.</p>
    <p>There is probably a huge difference in each components stylesheet. Sorry about that, but styling isnt the bread and butter this time round. Maybe in a future version.</p>
    <p>I would also, open up your console as I have left a bit of info accessable there.</p>
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
