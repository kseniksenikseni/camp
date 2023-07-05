<template>
  <div class="container">
    <div class="newss">
  <span class="news">Новости</span>
    </div>
    <hr class="hr">
  <div class="box">
    <my-button @click="funcLeft" class="left">
      <img src="../assets/Left.png" alt="" class="img">
    </my-button>
    <my-new class="my-new" v-for="new1 in arr" :new1="new1" :key="new1.id"/>
    <my-button @click="funcRight" class="right">
      <img src="../assets/Right.png" alt="" class="img">
    </my-button>

  </div>
  </div>
</template>

<script>
import MyButton from "@/components/MyButton.vue";
import MyNew from "@/components/MyNew.vue";
export default {
  components:{
    MyButton,
    MyNew
  },
  props:{
    arr:{
      type: Array
    }
  },
  methods:{
    funcRight(){
      this.$emit('moveR', this.arr)
    },
    funcLeft(){
      this.$emit('moveL', this.arr)
    }
  }
}
</script>

<style scoped>
.right, .left{
  background-color:  #1E3685;
  margin-top: 300px;
}
.box{
  display: flex;
  justify-content: space-between;
  margin-left: 0px;
  margin-top: -10px;
}
.container{
  background-color:  #1E3685;
  width:81.9% ;
  margin-left: 202px;
  margin-top: 15px;
  height: 800px;
}
.my-new{
  width: 1000px;
  margin-top:30px;
  margin-left: 20px;
  background-color: white;
  height: 615px;
  border-radius: 5px;
}

.news{
  color: white;
  font-size: 32px;
  margin-left: 610px;
}
.hr{
  margin: 20px 0;
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid #435583;
}
.newss{
  padding-top: 30px;
}
</style>