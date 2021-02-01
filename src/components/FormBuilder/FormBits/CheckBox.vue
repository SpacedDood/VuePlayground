<template>
  <div>
      {{FieldLabel}}
      <input type="checkbox" v-bind:checked="inputValue" v-on:change="updateForm">
  </div>
</template>

<script>
export default {
  name: 'CheckBox',
  props: {
    FieldName: String,
    value: {
      type: String,
      default: "false",
    },
    FieldLabel: String
  },
  data () {
    return {
      inputValue: false
    }
  },
  methods: {
    updateForm(e) {
      console.log(e)
      this.inputValue = !this.inputValue
      this.$emit('updateForm', [this.FieldName, this.inputValue])
    }
  },
  computed: {
    inputVal: {
      get() {
        return this.inputValue;
      },
      set(val) {
        this.inputValue = val
      }
    }
  }
}


</script>

<style>
</style>
