<template>
  <div class="SimpleArrayPlayground">

    <h1>Simple Array Playground</h1>

    <UploadPhoto/>

    <PrettyView v-if="prettyViewNo!=null" v-bind:dataSet="theArray[prettyViewNo]"/>

    <SearchArea v-bind:theArray="theArray" v-bind:showPrettyView="showPrettyView" v-bind:toggleCreateView="toggleCreateView"/>

    <CreateArea v-if="showCreateArea" v-bind:addDataToArray="addDataToArray" v-bind:toggleCreateView="toggleCreateView"/>

    <DataPreview v-if="showDataPreview" v-bind:theArray="theArray" v-bind:removeDataFromArray="removeDataFromArray"/>

    <div class="rawData">
      {{data}}
    </div>

  </div>
</template>

<script>

import SearchArea from './SearchArea.vue'
import CreateArea from './CreateArea/CreateArea.vue'
import DataPreview from './DataPreview.vue'
import PrettyView from './PrettyView/PrettyView.vue'
import UploadPhoto from "./UploadPhoto/UploadPhoto.vue"


export default {
  name: 'SimpleArrayPlayground',
  components: {
    SearchArea,
    CreateArea,
    DataPreview,
    PrettyView,
    UploadPhoto
  },
  data() {
    return {
      prettyViewNo: null,
      showCreateArea: false,
      showDataPreview: true,
      theArray: [
        {
          id: 1,
          name: "Alfred",
          age: 24,
          favoriteColor: "Blue"
        },
        {
          id: 2,
          name: "Bob",
          age: 15,
          favoriteColor: "Pink"
        },
        {
          id: 3,
          name: "Carol",
          age: 25,
          favoriteColor: "Green"
        },
        {
          id: 4,
          name: "Bobby Jr",
          age: 18,
          favoriteColor: "Pink"
        }
      ],
      lastId: 0
    }
  },
  created() {
    this.lastId = this.theArray.length;
  },
  methods: {
    showPrettyView(dataId) {
      console.log("got dataId: " + dataId)
      this.theArray.forEach((item, i) => {
        console.log("runthrough " + item.id)
        if (item.id == dataId) {
          this.prettyViewNo = i
          console.log("Found it!")
        }
        console.log(i)
      });
    },
    toggleCreateView() {
      this.showCreateArea = !this.showCreateArea
    },
    addDataToArray(submissionData) {
      this.lastId+=1
      submissionData.id = this.lastId;
      this.theArray.push(submissionData)
    },
    removeDataFromArray(id) {
      this.theArray.forEach((item, i) => {
        if (item.id == id) {
          this.theArray.splice(i, 1)
        }
      });
    }
  }
}
</script>


<style scoped>

</style>

<!-- TODO
Figure out a better way to hide/show windows management
-->
