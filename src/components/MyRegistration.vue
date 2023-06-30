<template>
  <span class="title">Регистрация</span>
  <div class="registration" >
    <div class="blocks-input">
    <label for="name">Имя:</label>
    <input type="text" id="name" v-model="post.name">
    </div>
    <div class="blocks-input">
    <label for="surname">Фамилия:</label>
    <input type="text" id="surname" v-model="post.surname">
    </div>
    <div class="blocks-input">
          <label for="login">Логин:</label>
          <input type="text" id="login" v-model="post.login">
        </div>
      <div class="blocks-input">
          <label for="password">Пароль:</label>
          <input type="text" id="password" v-model="post.password">
        </div>
    <div class="button_block">
      <my-button class="btn" @click="regUser">Регистрация</my-button>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/MyButton.vue";
export default {
  components: {
    MyButton
  },
  data(){
    return{
      post:{
        login:'',
        password:'',
        surname:'',
        name:'',
      }
    }
  },
  methods:{
    regUser(){
      this.$emit('create', this.post);
    }
  }

}
</script>

<style scoped>
.registration{
  display: flex;
  flex-direction: column;
  margin-top: 20px;

}

.blocks-input{
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}
input{
  width: 350px;
  height: 30px;
}
.title{
  font-size: 32px;
}
label{
  font-size: 18px;
  //font-family: 'Roboto';
  //font-weight: regular;
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