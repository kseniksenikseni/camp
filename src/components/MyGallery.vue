<template>
<div class="container">
  <div class="gallery">
    <span class="txt-gallery">
      Фотогалерея
    </span>
    <div class="block">
      <img class="a" src="../assets/a.jpg" alt="">
      <img class="a" src="../assets/b.jpg" alt="">
      <img class="a" src="../assets/c.jpg" alt="">
      <img class="a" src="../assets/c.jpg" alt="">
      <img class="a" src="../assets/a.jpg" alt="">

    </div>
    <my-button class="btn" @click="openF">Все фотографии</my-button>
  </div>
</div>
</template>
<script>
import MyButton from "@/components/MyButton.vue";
export default{
  components: {
    MyButton
  },
  props: {
    openFoto: {
      type: Boolean,
      default: false
    }
    },
  methods: {
    openF() {
      this.$emit('change2', this.openFoto);
    }
  }
}
</script>

<style scoped>
.container{
  width:81.9% ;
  background-color: #1E3685;
  margin-left: 202px;
}
.block{
  display: flex;
  justify-content: space-between;
  width: 1100px;
  margin-left: 100px;
}
.txt-gallery{
  color: white;
  font-size: 30px;
  margin-left: 600px;
}
.a{
  width: 18%;
}
.gallery{
  padding-top: 50px;
}
</style>