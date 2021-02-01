<template>
  <div>
      {{FieldLabel}}
      <input v-model="inputValue" v-on:input="updateForm">
  </div>
</template>

<script>
export default {
  name: 'SingleText',
  props: {
    FieldName: String,
    value: {
      type: String,
      default: "",
    },
    FieldLabel: String
  },
  data () {
    return {
      inputValue: ""
    }
  },
  methods: {
    updateForm() {
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
