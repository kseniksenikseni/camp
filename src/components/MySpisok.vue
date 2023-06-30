<template>
<div class="feed" v-if="statusUser">
  <my-feedback v-for="form in forms" :form="form" :key="form.id"/>
</div>
</template>

<script>
import MyFeedback from "@/components/MyFeedback.vue";
export default{
  components:{
    MyFeedback
  },
  props:{
    forms:{
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>