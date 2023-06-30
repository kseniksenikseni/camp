<template>
  <div class="block-teacher">
    <img class="img" :src="team1.imgTeacher" alt=""> <br>  <br>
    <span class="name">{{team1.nameTeacher}}</span> <br>
    <span class="txt">{{team1.txtTeacher}}</span>
  </div>
</template>

<script>
export default {
  props:{
    team1:{
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.block-teacher{
 width:700px;
}
.img{
  width: 310px;
  height: 310px;
}
.name{
  font-size: 18px;
  font-weight: bold;
  margin-left: 11px;
}
.txt{
  margin-left: 90px;
  font-size: 16px;
  margin-top: 10px;
}
</style>