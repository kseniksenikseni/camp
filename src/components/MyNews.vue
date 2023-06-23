<template>
  <div class="container">
    <div class="newss">
  <span class="news">Новости</span>
    </div>
    <hr class="hr">
  <div class="box">
    <my-button @click="funcLeft" class="left">
      <img src="../assets/Left.png" alt="" class="img-left">
    </my-button>
    <my-new class="my-new" v-for="new1 in arr" :new1="new1" :key="new1.id"/>
    <my-button @click="funcRight" class="right">
      <img src="../assets/Right.png" alt="" class="img-right">
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
  margin-top: 200px;
}
.box{
  display: flex;
  justify-content: space-between;
}
.container{
  background-color:  #1E3685;
  width:81.9% ;
  margin-left: 202px;
  margin-top: 15px;
  height: 500px;
}
.my-new{
  margin-top: 20px;
  margin-right: 13px;
}
.news{
  color: white;
  font-size: 30px;
  margin-left: 600px;
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


<!--let arr = ['./img/1.jpg','./img/2.jpg','./img/3.jpg','./img/4.jpg','./img/5.jpg','./img/6.jpg','./img/7.jpg',-->
<!--'./img/8.jpg','./img/9.jpg','./img/10.jpg','./img/11.jpg','./img/12.jpg']-->

<!--let btn1 = document.querySelector('.button1')-->
<!--let btn2 = document.querySelector('.button2')-->
<!--let mas_img = document.querySelectorAll('.img_foto')-->

<!--btn2.addEventListener('click', (e) =>{-->
<!--arr.push(arr[0])-->
<!--arr.shift(arr[0])-->
<!--mas_img[0].src = arr[0]-->
<!--mas_img[1].src = arr[1]-->
<!--mas_img[2].src = arr[2]-->
<!--})-->
<!--btn1.addEventListener('click', (e) =>{-->
<!--arr.unshift(arr[arr.length-1])-->
<!--arr.pop(arr[arr.length-1])-->
<!--mas_img[0].src = arr[0]-->
<!--mas_img[1].src = arr[1]-->
<!--mas_img[2].src = arr[2]-->
<!--})-->

<!--let cont = document.querySelector('.container2')-->
<!--let img_big = document.querySelector('.img_big')-->
<!--let click_save = arr[0]-->

<!--cont.addEventListener('mouseover', (e) =>{-->

<!--if(e.target.tagName === "IMG"){-->
<!--img_big.src = e.target.src-->
<!--}-->
<!--})-->

<!--cont.addEventListener('click', (e) =>{-->

<!--if(e.target.tagName === "IMG"){-->
<!--img_big.src = e.target.src-->
<!--click_save = e.target.src-->
<!--}-->
<!--})-->

<!--cont.addEventListener('mouseout', (e) =>{-->
<!--img_big.src = click_save-->

<!--})-->

<!--cont.addEventListener('mousedown', (e) =>{-->

<!--if(arr.length>3){-->

<!--if(e.button === 2){-->
<!--let c = 0-->
<!--let del_img = e.target.getAttribute("src")-->
<!--for(let i=0; i<arr.length; i++){-->
<!--if(arr[i] === del_img){-->
<!--c = i-->
<!--break-->
<!--}-->
<!--}-->
<!--arr.splice(c, 1)-->
<!--mas_img[0].src = arr[0]-->
<!--mas_img[1].src = arr[1]-->
<!--mas_img[2].src = arr[2]-->
<!--console.log(arr)-->
<!--}}-->

<!--})-->
