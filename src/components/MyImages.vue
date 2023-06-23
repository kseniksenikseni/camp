<template>
<div class="container">
<!--  <img class="img" :src="img1.imgImages" alt="">-->

</div>
</template>

<script>
export default {
  props:{
    img1:{
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>


<!--<template>-->
<!--  <form @submit.prevent>-->
<!--    <h4>Создание поста</h4>-->
<!--    <input placeholder="Название" v-model="post.title">-->
<!--    <input placeholder="Описание" v-model="post.body">-->
<!--    <my-button class="btn-add" @click="addPost">Добавить</my-button>-->
<!--  </form>-->
<!--</template>-->

<!--<script>-->
<!--import MyButton from "@/components/MyButton";-->
<!--export default {-->
<!--  components: {MyButton},-->
<!--  data() {-->
<!--    return {-->
<!--      post: {-->
<!--        title: '',-->
<!--        body: '',-->
<!--      }-->
<!--    }-->
<!--  },-->
<!--  methods: {-->
<!--    addPost() {-->
<!--      this.post.id = Date.now()-->
<!--      this.$emit('create', this.post)-->
<!--      this.post = {-->
<!--        title: '',-->
<!--        body: ''-->
<!--      }-->
<!--    }-->
<!--  }-->
<!--}-->
<!--</script>-->

<!--<style scoped>-->
<!--form{-->
<!--  display: flex;-->
<!--  flex-direction: column;-->
<!--}-->
<!--input{-->
<!--  width: 430px;-->
<!--  margin-left: 20px;-->
<!--  border: 1px solid cadetblue;-->
<!--  padding: 10px 15px;-->
<!--  margin-top: 15px;-->
<!--}-->
<!--.btn{-->
<!--  margin-top: 15px;-->
<!--  align-self: flex-end;-->
<!--  padding: 10px 15px;-->
<!--  background: none;-->
<!--  color: teal;-->
<!--  border: 1px solid cadetblue;-->
<!--}-->
<!--h4{-->
<!--  text-align: center;-->
<!--}-->
<!--.btn-add{-->
<!--  align-self: flex-end;-->
<!--}-->
<!--</style>-->