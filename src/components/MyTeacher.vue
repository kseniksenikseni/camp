<template>
  <div class="block-teacher">
    <img class="img" :src="team1.imgTeacher" alt=""> <br>
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
.img{
  width: 250px;
  height: 250px;
}

</style>