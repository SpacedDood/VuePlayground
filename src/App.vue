<template>
  <div class="wrap">
    <HelloWorld msg="Doods First Vue Components"/>
    <SearchArea v-if="showPlayground"/>
    <SimpleArrayPlayground />
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SimpleArrayPlayground from './components/SimpleArrayPlayground.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    SimpleArrayPlayground
  },
  data() {
    return {
      showPlayground: false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

div {
  margin: 10px;
}
</style>
