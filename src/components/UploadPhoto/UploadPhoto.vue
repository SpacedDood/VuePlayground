<template>
  <div class="cameraArea">
    <h2>This is the Camera Area!</h2>
    <p>
      The First of many component collections I will be working on.
    </p>

    <input type="file" v-on:change="previewFiles($event.target)"/>

    <div class="imgDisplay" v-if="imgBase64Data">
      <img v-bind:src="imgBase64Data">
    </div>

    <div class="center" v-if="imgBase64Data">
      <div class="btn" v-on:click="confirmedUpload">
        <span> Confirm Upload </span>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'UploadPhoto',
  props: {
    msg: String
  },
  data() {
    return {
      fileArea: false,
      imgBase64Data: null
    }
  },
  methods : {
    previewFiles(e) {
      this.fileArea = e;
      /* any way to get the object input */
      let reader = new FileReader();
      if(e.files[0]) {
          reader.onload = () => {
          var imgBase64 = reader.result;
          console.log(imgBase64);
          this.imgBase64Data = imgBase64
          //your request
        }
        console.log(e.files[0])
        reader.readAsDataURL(e.files[0]);

      }
    },
    confirmedUpload() {
      console.log("Upload Confirmed... ship it out")
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.cameraArea {
  border: 1px solid black;
}

.imgDisplay {
  width: 400px;
  height: 400px;
  display: block;
  border: 2px;
  margin: auto;
  vertical-align: middle;
}

.imgDisplay img {
  max-width: 300px;
  max-height: 500px;
}

.btn {
  background-color: #d3ffd4;
  max-width: 300px;
  padding: 5px;
  display: block;
  margin: auto;
  border: 1px solid black;
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
