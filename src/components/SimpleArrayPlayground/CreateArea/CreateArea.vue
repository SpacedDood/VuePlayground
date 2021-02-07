<template>
  <div class="createArea">
    <h2>
      The Create Area.
    </h2>
    <div class="formSection">

      <form>
        <div class="fieldArea">
          <label for="name">Name: </label>
          <input type="text" name="name" v-model="name"/>
        </div>

        <div class="fieldArea">
          <label for="name">Age: </label>
          <input type="text" name="age" v-model="age"/>
        </div>

        <div class="fieldArea">
          <label for="name">favorite Color: </label>
          <input type="text" name="favoriteColor" v-model="favoriteColor"/>
        </div>

        <div class="buttonArea">
          <div class="btn" v-on:click="startSubmission">Submit</div>
        </div>
      </form>

    </div>

    <div class="close" v-on:click="toggleCreateView">
      Close
    </div>

  </div>
</template>

<script>
export default {
  name: 'CreateArea',
  data () {
    return {
      name:"",
      age:"",
      favoriteColor:""
    }
  },
  props: {
    addDataToArray: { type: Function },
    toggleCreateView: { type: Function }
  },
  methods: {
    startSubmission () {

      //Do some custom validation and then add it to array
      var submissionData = {}

      //Name
      console.log(this.name)
      submissionData.name = this.name;
      //Age
      console.log(this.age)
      submissionData.age = this.age;
      //Favorite Color
      console.log(this.favoriteColor)
      submissionData.favoriteColor = this.favoriteColor;

      //ship off said array
      this.addDataToArray(submissionData)

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.createArea {
  position: relative;
  border: 2px solid;
}

.formSection {
  text-align: left;
}

</style>
