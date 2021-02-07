<template>
  <div class="searchArea">
    <h2>SearchArea</h2>
    <p>Im the Search Area!</p>
    <div class="inputField">
      <form autocomplete="off">
        <input name="search" v-on:keyup="searchUpdated($event.target.value)" placeholder="Search"/>
      </form>
    </div>

    <div class="results" v-if="searching">

      <!--Loading Symbol-->
      <div class="resultThing loading" v-if="isLoading">
        <span>Loading...</span>
      </div>

      <!--Results area-->
      <div class="resultsArea" v-else>
        <div class="resultsArea" v-if="results.length>0">
          <div class="resultThing" v-bind:key="arrayObject.id" v-for="arrayObject in results" v-on:click="showPrettyView(arrayObject.id);  hideSearchOptions();">
            <span>{{arrayObject.name}}</span>
          </div>
        </div>
        <div class="resultsArea" v-else>
          <div class="resultThing">
            <span>No Results Found :(</span>
          </div>
        </div>
      </div>

      <!--Create new-->
      <div class="resultThing createNew" v-on:click="toggleCreateView(); hideSearchOptions();">
        <span>+ Create New</span>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'SearchArea',
  props: {
    toggleCreateView: { type: Function },
    showPrettyView: {type: Function },
    theArray: { type: Array }
  },
  data() {
    return {
      searching: false,
      results:[],
      isLoading: false,
      timer: null
    }
  },
  methods: {
    searchUpdated(searchValue) {
      this.searching = true
      clearInterval(this.timer)
      this.isLoading = true
      this.timer = setInterval(this.timerFinished, 1000, searchValue)
    },
    timerFinished(searchValue) {
      this.searchArray(searchValue)
      this.isLoading = false
      clearInterval(this.timer)
    },
    searchArray(searchValue) {
      //This is where you would search for Data
      //And push results to the results array
      this.results = []
      this.theArray.forEach((item) => {
        if (item.name.toLowerCase().includes(searchValue.toLowerCase())) {
          this.results.push(item)
        }
      });
    },
    hideSearchOptions() {
      this.searching = false
    }
  }
}
</script>

<style scoped>
.searchArea {
  position: relative;
  border: 2px solid;
}

.inputField input {
  border: 2px solid grey;
  border-radius: 3px;
  padding: 5px;
  box-sizing: border-box;
  width: 100%;
  margin: 0px;
}

.results {
  display: block;
  position: absolute;
  width: 100%;
  margin: -10px 0 0;
  padding: 0 20px;
  box-sizing: border-box;
  z-index: 5;
}

.resultsArea {
  margin: 0;
  padding: 0;
}

.resultThing {
  background: grey;
  margin: 0 5px;
  border: 1px solid black;
  padding: 5px;
  box-sizing: content-box;
}
</style>


<!-- TODO
+ Add a custom click event something along the lines of custom directives
I tried adding @focusout, but it was being triggered even when clicking on search area :(
heres some source if you are feeling brave - https://stackoverflow.com/questions/36170425/detect-click-outside-element

+ Hide the autocomplete nonsense
-->
