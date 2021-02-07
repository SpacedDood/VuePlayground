<template>
  <div class="wrap">
    <HelloWorld msg="Doods First Vue Components"/>

    <div class="navWrap">

      <NavigationMenu :toggleDisplay="toggleDisplay" />

      <div class="displayArea">
          <FormBuilder v-if="showForm"/>
          <SimpleArrayPlayground v-if="showPlayground"/>
          <UploadPhoto v-if="showPhotoUpload"/>
      </div>

    </div>

  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SimpleArrayPlayground from './components/SimpleArrayPlayground/SimpleArrayPlayground.vue'
import FormBuilder from './components/FormBuilder/FormBuilder.vue'
import NavigationMenu from './components/Navigation/NavigationMenu.vue'
import UploadPhoto from "./components/UploadPhoto/UploadPhoto.vue"

export default {
  name: 'App',
  components: {
    HelloWorld,
    NavigationMenu,
    SimpleArrayPlayground,
    FormBuilder,
    UploadPhoto
  },
  data() {
    return {
      showPlayground: false,
      showForm: true,
      showPhotoUpload: false
    }
  },
  methods: {
    toggleDisplay : function(label) {
      //I know I know. This is shit. But its makedo.
      //I should turn this whole thing into its own component which does all of this. But I cannae be arsed right now.
      //Bigger fish to fry.
      if (label == "form") {
        this.showForm = true;
        this.showPlayground = false;
        this.showPhotoUpload = false;
      }
      if (label == "array") {
        this.showForm = false;
        this.showPlayground = true;
        this.showPhotoUpload = false;
      }
      if (label == "photo") {
        this.showForm = false;
        this.showPlayground = false;
        this.showPhotoUpload = true;
      }
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

.navWrap {
  display: flex;
}

.displayArea {
  flex-grow: 5;
}

</style>
