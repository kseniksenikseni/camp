<template>
  <div class="container">
    <div class="team">
      <span class="news">Наша команда</span>
    </div>
    <div class="box">
      <my-button @click="funcLeft" class="left">
        <img src="../assets/fi-sr-caret-left.png" alt="" class="img-left">
      </my-button>
      <my-teacher class="my-teacher" v-for="team1 in arr" :team1="team1" :key="team1.id"/>
      <my-button @click="funcRight" class="right">
        <img src="../assets/fi-sr-caret-right.png" alt="" class="img-right">
      </my-button>

    </div>
  </div>
</template>

<script>
import MyButton from "@/components/MyButton.vue";
import MyTeacher from "@/components/MyTeacher.vue";
export default {
  components:{
    MyTeacher,
    MyButton,
  },
  props:{
    arr:{
      type: Array
    }
  },
  methods:{
    funcRight(){
      this.$emit('movesR', this.arr)
    },
    funcLeft(){
      this.$emit('movesL', this.arr)
    }
  }
}
</script>

<style scoped>
.right, .left{
  background-color: white;
  margin-top: 200px;
}
.box{
  display: flex;
  justify-content: space-between;
}
.container{
  background-color: white;
  width:81.9% ;
  margin-left: 202px;
  margin-top: 20px;
}
.my-teacher{
  margin-top: 50px;

}
.news{
  font-size: 30px;
  margin-left: 600px;
}
.team{
  padding-top: 50px;
}
</style>