<template>
  <div class="block-news">
    <img class="img" :src="new1.imgNew" alt=""> <br>
    <span class="txt">{{new1.infNew}}</span>
  </div>
</template>

<script>
export default {
  props:{
    new1:{
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.img{
  width: 270px;
  height: 270px;
}
.txt{
  color: white;
}
</style>