<template>
  <span class="title">Авторизация</span>
  <div class="autho_block">
    <div class="blocks-input">
      <label for="login">Логин:</label>
      <input type="text" id="login" v-model="user.login">
    </div>
    <div class="blocks-input">
      <label for="password">Пароль:</label>
      <input type="text" id="password" v-model="user.password">
    </div>
    <my-button class="btn" @click="autho">Авторизоваться</my-button>
  </div>
</template>

<script>
import MyButton from "@/components/MyButton";
export default {
  components: {
    MyButton
  },
  data(){
    return{
      user:{
        login:'',
        password:'',
      }
    }
  },
  methods:{
    autho(){
      this.$emit('find',this.user);
    }
  }
}
</script>

<style scoped>
.blocks-input{
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}
input{
  width: 350px;
  height: 30px;
}
.autho_block{
  display: flex;
  flex-direction: column;
  margin-top: 20px;
}
label{
  font-size: 18px;
  //font-family: 'Roboto';
  //font-weight: regular;
}
.title{
  font-size: 32px;
  //font-family: 'Roboto';
}

.btn{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 180px;
  height: 45px;
  background-color: #3F51B5;
  color: white;
  border-radius: 3px;
  font-size: 18px;
  //font-family: 'Roboto';
  //font-weight: regular;
  margin-left: 160px;
  margin-top: 50px;
}

</style>