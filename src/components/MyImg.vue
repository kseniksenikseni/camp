<template>
  <div class="container">
    <div class="foto">
      <span class="txt-foto">Фотогалерея</span>
    </div>
    <div class="box">
<!--      <my-images class="my-images" v-for="img1 in img1" :img1="img1" :key="img1.id"/>-->
      <div class="box1">
      <img class="a" src="../assets/a.jpg" alt="">
      <img class="a" src="../assets/a.jpg" alt="">
      <img class="a" src="../assets/a.jpg" alt="">
      <img class="a" src="../assets/a.jpg" alt="">
      </div>
      <div class="box1">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
      </div>
      <div class="box1">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
      </div>
      <div class="box1">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
      </div>
      <div class="box1">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
        <img class="a" src="../assets/a.jpg" alt="">
      </div>



    </div>
  </div>
</template>

<script>
// import MyImages from "@/components/MyImages.vue";
export default {
  components:{
    // MyImages
  },
  props:{
    arr:{
      type: Array
    }
  },
}
</script>

<style scoped>
.a{
  width: 22%;
  margin-left: 20px;
}
.txt-foto{
  font-size: 25px;
  margin-left: 340px;
}
.box{
  width:800px;
  height: 550px;
  overflow-y: scroll;
  margin-top: 40px;
}
</style>