<template>
  <div class="prettyView">
    <h2>Pretty Viewing: {{dataSet? dataSet.id : "Error"}}</h2>

    <div class="theView" v-if="dataSet">
      <p><span>ID:</span> {{dataSet.id}}</p>
      <p><span>Name:</span> {{dataSet.name}}</p>
      <p><span>Age:</span> {{dataSet.age}}</p>
      <p><span>Favorite Color:</span> {{dataSet.favoriteColor}}</p>
    </div>

    <div class="error" v-else>
      <p>Data could not be found</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'PrettyView',
  props: {
    dataSet: { type: Array }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.prettyView {
  border: 2px solid;
}

.theView {
  text-align: left;
}

</style>
