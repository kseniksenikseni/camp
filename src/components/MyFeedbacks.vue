<template>
  <div class="container">
<!--    <div class="block"><span class="feed">Отзывы</span></div>-->
<!--    <hr class="hr">-->
    <my-feedback
        v-for="form in forms"
        :form="form"
        :key="form.id"
        @remove="$emit('remove', form)"
    />
  </div>
</template>

<script>
import MyFeedback from "@/components/MyFeedback.vue";
export default {
  components: {
    MyFeedback
  },

  props: {
    forms: {
      type: Array,
      required: true
    }
  }
}

</script>

<style scoped>
.feed{
  font-size: 32px;
  margin-left: 600px;

}
.container{
  width:81.9% ;
  margin-left: 202px;
  margin-top: 20px;
  height: 150px;
  background-color: white;

}
.block{
  padding-top: 30px;
}
.hr {
  margin: 20px 0;
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid lightgrey;
}
</style>