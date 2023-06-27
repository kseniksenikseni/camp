<template>
  <div class="feed">
    <div>
<!--      <div>{{form.name}}</div>-->
      <div>{{form.feedback}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    form:{
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>