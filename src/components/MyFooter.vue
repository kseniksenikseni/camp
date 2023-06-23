<template>
<footer>
  <span class="school">
     Муниципальное бюджетное <br> общеобразовательное учреждение <br> “Школа№123”
  </span>
  <div class="contacts">
    <div class="contct">
      <div class="inf1">
        <img class="a marker" src="../assets/fi-sr-marker-white.png" alt="">
        <span class="inf2">603135, г. Нижний Новгород, ул. Дружбы, д. 50</span>
      </div>
      <div class="inf1 bb">
        <img class="a" src="../assets/Vector-white.png" alt="">
        <span class="inf2">(831) 234-2-123</span>
      </div>
    </div>
      <div class="contct">
        <div class="inf1 bb">
          <img class="pin" src="../assets/fi-ss-envelope-white.png" alt="">
          <span class="inf2">s123_nn@mail.52gov.ru</span>
        </div>
        <div class="inf1 bb">
          <img class="pin" src="../assets/vk-white.png" alt="">
          <span class="inf2">Вконтакте</span>
        </div>
      </div>
      </div>
</footer>
</template>
<script setup>

</script>

<style scoped>
footer{
  background-color: #1E3685;
  width: 81.8%;
  height: 200px;
  margin-left: 202px;
  display: flex;
  justify-content: space-between;
}
.inf2{
  margin-left: 5px;
  color: white;
}
.school{
  font-size: 24px;
  color: white;
}
.contacts{
  display: flex;
  justify-content: space-between;
}
</style>