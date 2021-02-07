<template>
  <div class="hello">
    <h1>EZ Nav</h1>
    <p>This is my makeshift Navigation:</p>

    <div class="item" v-on:click="toggleDisplay('form')" >Form Builder</div>
    <div class="item" v-on:click="toggleDisplay('array')">Array Playground</div>
    <div class="item" v-on:click="toggleDisplay('photo')">Photo Upload</div>

  </div>
</template>

<script>
export default {
  name: 'NavigationMenu',
  props: {
    toggleDisplay: { type: Function },
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

.item {
  text-decoration: underline;
}

.item:hover {
  cursor:pointer;
  text-decoration: none;
}

</style>
