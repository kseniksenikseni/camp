<template>
  <div class="block-news">
    <img class="img" :src="new1.imgNew" alt=""> <br>
    <div class="text">
      <span class="txt">{{new1.infNew}}</span>
    </div>
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
  width: 500px;
  height: 57%;
  margin-left: 20px;
  margin-top: 20px;
}
.txt{
  margin-top: 15px;
font-size: 17px;
  text-indent: 1.5px;
}
.text{
  width: 500px;
  margin-top: 10px;
  border-color: white;
  margin-left: 20px;
  text-align: justify;
}
</style>