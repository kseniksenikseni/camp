<template>
<footer>
  <div class="foot">
    <span class="school">
     Муниципальное бюджетное <br> общеобразовательное учреждение <br>  “Школа №123”
  </span>
    <div class="contacts">
      <div class="contct c">
        <div class="inf1">
          <img class="a marker" src="../assets/fi-sr-marker-white.png" alt="">
          <span class="inf2">603135, г. Нижний Новгород, ул. Дружбы, д. 50</span>
        </div>
        <div class="inf1 bb">
          <img class="a aa" src="../assets/Vector-white.png" alt="">
          <span class="inf2">(831) 234-2-123</span>
        </div>
      </div>
      <div class="contct">
        <div class="inf1 bb">
          <img class="pin" src="../assets/fi-ss-envelope-white.png" alt="">
          <span class="inf2">s123_nn@mail.52gov.ru</span>
        </div> <br>
        <div class="inf1 bb">
          <img class="pin" src="../assets/vk-white.png" alt="">
          <a href="https://vk.com/school123nn">
            <span class="inf2 gg">Вконтакте</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</footer>
</template>
<script setup>

</script>

<style scoped>
.foot{
  background-color: #1E3685;
  width: 81.9%;
  height: 119px;
  margin-left: 202px;
  display: flex;
 margin-bottom: 15px;
  justify-content: space-between;

}
.inf2{
  margin-left: 10px;
  color: white;
}
.inf2{
  font-size: 15px;
}
.a{
  width: 4.5%;
}
.aa{
  width: 4%;
  margin-top: 10px;
}
.gg{
  text-decoration:underline;
}
.school{
  font-size: 22px;
  color: white;
  margin-left: 100px;
  margin-top:10px;
}
.pin{
  width: 10%;
}
.hr{
  margin: 20px 0;
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid #435583;
}
.contacts{
  display: flex;
  justify-content: space-between;
  margin-right: 100px;
  margin-top: 20px;
}
.c{
  margin-right: 20px;
}
</style>