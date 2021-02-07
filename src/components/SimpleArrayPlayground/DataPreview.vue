<template>
  <div class="dataPreview">
    <h2>Data Preview</h2>
    <table>
      <thead>
        <td>ID</td>
        <td>Name</td>
        <td>Age</td>
        <td>favoriteColor</td>
        <td>Remove</td>
      </thead>
      <tr v-for="arrayObject in theArray" v-bind:key="arrayObject.id">
        <td>{{arrayObject.id}}</td>
        <td>{{arrayObject.name}}</td>
        <td>{{arrayObject.age}}</td>
        <td>{{arrayObject.favoriteColor}}</td>
        <td v-on:click="removeDataFromArray(arrayObject.id)">X</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'DataPreview',
  props: {
    removeDataFromArray: { type: Function },
    theArray: { type: Array }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.dataPreview {
  border: 2px solid;
}

table {
  width: 100%;
}

table tr td {
  border: 1px solid darkGrey;
}
</style>
