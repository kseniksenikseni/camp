<template>
  <div class="container">
    <div class="color"></div>
  <div class="header">
    <div class="header1">
      <img class="log" src="../assets/Emblema_shkoly.png" alt="logo">
      <div class="school">
      <span class="skola">
    Муниципальное бюджетное <br> общеобразовательное учреждение <br> “Школа№123”
  </span>
    </div>
    <div class="header2">
      <div class="header3">
        <div class="inf">
          <div class="inf1">
                      <img class="a marker" src="../assets/fi-sr-marker.png" alt="">
            <span class="inf2">603135, г. Нижний Новгород, ул. Дружбы, д. 50</span>
          </div>
          <div class="inf1 bb">
                      <img class="a" src="../assets/Vector.png" alt="">
            <span class="inf2">(831) 234-2-123</span>
          </div>
          <div class="inf1 bb">
                      <img class="pin" src="../assets/fi-ss-envelope.png" alt="">
            <span class="inf2">s123_nn@mail.52gov.ru</span>
          </div>
        </div>
        <div class="buttons">
          <my-button class="reg" @click="openR">Регистрация</my-button>
          <my-button class="reg aut" @click="openAutho">Авторизация</my-button>
        </div>
      </div>
    </div>
  </div>
  </div>
  </div>
  </template>

<script>
import MyButton from "@/components/MyButton.vue";
export default {
  components: {
    MyButton
  },
  props: {
    openReg: {
      type: Boolean,
      default: false
    },
    openAuthorization:{
      type:Boolean,
      default:false
    },
  },
  methods: {
    openR() {
      this.$emit('change1', this.openReg);
    },
    openAutho(){
      this.$emit('open2',this.openAuthorization);
    }
  }
}
</script>

<style scoped>
.container{
  background-color: white;
  width: 81.8%;
  height: 190px;
  margin-left: 202px;
  margin-top: 20px;
}
.buttons{
  display: flex;
  flex-direction: column;

}
.skola{
  font-size: 23px;
  font-family: Arial;
}
.reg{
  background-color:  #1E3685;
  border-radius: 2px;
  color: white;
}
.header{
  display: flex;
  justify-content: space-between;
  margin-left: 60px;
  padding-top: 20px;
  //width: 1600px;
}
.color{
  background-color: #1E3685;
  height: 30px;
}
span{
  font-size: 18px;
  //font-family:'Roboto';
  font-family: Arial;
  line-height: 1.5;
}
.header3{
  display: flex;
  justify-content: space-between;
}
.bb{
  margin-top: 9px;
}
.inf2{
  margin-left: 5px;
  font-family: Arial;
}

.reg{
  height: 40px;
  margin-top: 0px;
  margin-left: 20px;
}
.log{
  width:130px;
  margin-top: -10px;
}
.pin{
  width: 4%;
}
.a{
  width: 3.8%;
}
.aut{
  margin-top: 20px;
}
.header1{
  display: flex;
  justify-content: space-between;
  width: 81%;

}
.school{
  margin-top: -3px;
}
.header3{
  width: 135%;
}
.header2{
  width: 44%;
}
</style>