<template>
<div class="container">
  <div class="gallery">
    <span class="txt-gallery">
      Фотогалерея
    </span>
    <hr class="hr1">
    <div class="block">
      <img class="a" src="https://sun9-71.userapi.com/impg/0o6j0DYWoTrqY5gb0iA0kWlOfyYjudOWtrpHXQ/gwAB7kpRK0M.jpg?size=810x1080&quality=96&sign=60541a09e95525e73c9beb3c346399f0&type=album" alt="">
            <img class="a" src="https://sun59-1.userapi.com/impg/Vvydhek4KbuQjhIzQWsgBqZI4kTONQ4OUAv_Aw/ad_0CssXQmE.jpg?size=810x1080&quality=96&sign=d15382cde3db333996f698e7f73598e4&type=album" alt="">
            <img class="a" src="https://sun59-2.userapi.com/impg/lrexSZJUfepuLRMHw5LyN3kh7XNKBWFq7tr-xA/UAH7qIKHgbI.jpg?size=810x1080&quality=96&sign=ba5f1dc86269532c9068a06b9160519b&type=album" alt="">
            <img class="a" src="https://sun9-33.userapi.com/impg/AmKuQERigu1tPUylLokYb4Fp79Re-mxEhtxOfg/tIPUUagwBNM.jpg?size=810x1080&quality=96&sign=d8ea42b2f1a3604e314abc879b32fc98&type=album" alt="">


    </div>
    <my-button class="btn" @click="openF">Все фотографии</my-button>
    <hr class="hr">
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
  margin-top: 20px;
  height: 630px;
}
.hr{
  margin-top: 40px;
  height: 0;
  border: none;
  border-top: 1px solid #435583;
}
.btn{
  margin-left: 541px;
  width: 219px;
  height: 45px;
  border-radius: 5px;
  margin-top: 50px;
}
.hr1{
  margin: 20px 0;
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid #435583;
}
.block{
  display: flex;
  justify-content: space-between;
  width: 1100px;
  margin-left: 100px;
  margin-top: 40px;
}
.txt-gallery{
  color: white;
  font-size: 30px;
  margin-left: 580px;

}
.a{
  width: 23%;
  border-radius: 5px;
  border: 3px solid #fff;
}

.gallery{
  padding-top: 30px;
}
</style>