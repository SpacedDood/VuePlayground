<template>
  <div class="formBuilder">
    <h2>
      EZ FormBuilder
    </h2>
    <div class="formSection">

      <form>

        <SingleText FieldName="name" FieldLabel="Name of Minion:" v-model="inputValue" v-on:updateForm="updateSingleText" />

        <SingleText FieldName="email" FieldLabel="Email of Minion:" v-model="inputValue" v-on:updateForm="updateSingleText" />


        <CheckBox FieldName="active" FieldLabel="Working?:" v-model="inputValue" v-on:updateForm="updateCheckBox" />

        <SingleText FieldName="job" FieldLabel="Job of Minion:" v-model="inputValue" v-on:updateForm="updateSingleText" />

        <SubmitButton FieldLabel="Yeet" v-on:click="submit()" />

      </form>

    </div>

  </div>
</template>

<script>


import SingleText from "./FormBits/SingleText.vue"
import SubmitButton from "./FormBits/SubmitButton.vue"
import CheckBox from "./FormBits/CheckBox.vue"
import axios from 'axios';

export default {
  name: 'FormBuilder',
  components: {
    SingleText,
    CheckBox,
    SubmitButton
  },
  data () {
    return {
      ezSingleText: [],
      ezCheckBox: []
    }
  },
  props: {
  },
  methods: {
    updateSingleText(value) {
      var found = false;
      this.ezSingleText.forEach((item) => {
        if (item.fieldName == value[0]) {
          item.fieldValue = value[1];
          found = true;
        }
      });
      if (!found) {
        this.ezSingleText.push({fieldName: value[0], fieldValue: value[1]})
      }
    },

    updateCheckBox(value) {
      var found = false;
      this.ezCheckBox.forEach((item) => {
        if (item.fieldName == value[0]) {
          item.fieldValue = value[1];
          found = true;
        }
      });
      if (!found) {
        this.ezCheckBox.push({fieldName: value[0], fieldValue: value[1]})
      }
    },
    submit () {
      //Validation before this?

      //Send it
      this.startSubmission()
    },
    startSubmission () {

      //Do some custom validation and then add it to array
      var submissionData = []

      //Loop thru all SingleText
      this.ezSingleText.forEach((item) => {
        submissionData.push([item.fieldName, item.fieldValue])
      });

      //Loop thru all checkbox
      this.ezCheckBox.forEach((item) => {
        submissionData.push([item.fieldName, item.fieldValue])
      });

      var JSONData = JSON.stringify(submissionData)

      var DataPacket = {data: JSONData}

      //ship off said array
      //console.log("startShipping", JSONData, JSON.parse(JSONData))
      this.shipIt(DataPacket)

    },
    shipIt(dataToShip) {
      console.log("DataReceived", dataToShip)
      axios.post( 'http://localhost:3000/minions', dataToShip )
      .then(data => {
        console.log({ message: 'Request received!', data })
      })
      .catch(err => console.log(err))

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  .formBuilder {
    position: relative;
    border: 2px solid;
  }

  .formSection {
    text-align: left;
  }

</style>
