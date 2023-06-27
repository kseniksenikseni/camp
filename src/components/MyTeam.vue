<template>
  <div class="container">
    <div class="team">
      <span class="news">Команда педагогов</span>
    </div>
    <hr class="hr">
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
  margin-top: 150px;
}

.box{
  display: flex;
  justify-content: space-between;
  margin-left: 0px;
  margin-top: -30px;
}
.container{
  background-color: white;
  width:81.9% ;
  margin-left: 202px;
  margin-top: 20px;
  height: 550px;
}
.hr{
  margin: 20px 0;
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid lightgrey;
  //border-top: 1px solid rgba(9, 9, 9, 0.99);
}
.my-teacher{
  margin-top: 50px;
  margin-left: 30px;
}
.news{
  font-size: 32px;
  margin-left: 540px;
}
.team{
  padding-top: 30px;
}
</style>