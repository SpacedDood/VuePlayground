<template>
  <div class="fieldArea">
    <div type="submit" name="name">{{FieldLabel}}</div>
  </div>
</template>

<script>
export default {
  name: 'SubmitButton',
  props: {
    FieldLabel: String
  },
}
</script>

<style>
</style>
