<template>
  <body>
  <div class="container">
  <my-header @change1="openR" @open2="openA"/>
  <div class="reg-auto">
    <my-dialog v-model:show="openRegistration">
      <my-registration @create="regUser"/>
    </my-dialog>
    <my-dialog v-model:show="openAuthorization">
      <my-authorization @find="authoUser"/>
    </my-dialog>
  </div>
  <img class="schol" src="https://sun9-18.userapi.com/impg/vZgZgZiayIJSDbUuba--5SlF_5Ptx_ZUpQXdyg/GryLTgKFn6M.jpg?size=1280x377&quality=96&sign=5cb669bf14507ffbdc107f75c9c77b4a&type=album" alt="">
  <my-news :arr="blockNews1" @moveR="funcMoveR" @moveL="funcMoveL"/>
    <my-team  :arr="blockTeam1" @movesR="funcMoveRight" @movesL="funcMoveLeft"/>
    <my-gallery @change2="openF"/>
    <my-dialog-gallery v-model:show="openFoto">
      <my-img />
    </my-dialog-gallery>
<!--      <my-gallery @change1="openF">-->
<!--       <my-img :arr="blockImages"></my-img>-->
<!--      </my-gallery>-->
    <my-footer/>
<!--    <my-dialog-gallery v-model:show="dialogVisible">-->
<!--      <post-form @create="addPost"/>-->
<!--    </my-dialog-gallery>-->
  </div>
  </body>
</template>

<script>
import MyHeader from "@/components/MyHeader.vue";
import MyRegistration from "@/components/MyRegistration.vue";
import MyDialog from "@/components/MyDialog.vue";
import MyAuthorization from "@/components/MyAuthorization.vue";
import MyNews from "@/components/MyNews.vue";
import MyTeam from "@/components/MyTeam.vue";
import MyGallery from "@/components/MyGallery.vue";
import MyImg from "@/components/MyImg.vue";
import MyFooter from "@/components/MyFooter.vue";
import MyDialogGallery from "@/components/MyDialogGallery.vue";
export default {
  components:{
    MyDialogGallery,
    MyFooter,
    MyImg,
    MyGallery,
    MyTeam,
    MyNews,
    MyHeader,
    MyRegistration,
    MyDialog,
    MyAuthorization
  },
  data(){
    return{
      openRegistration: false,
      openAuthorization: false,
      openFoto: false,
      objectAuthoUser:{},
      border1: 0,
      border2: 3,
      blockNews:[
        {
        imgNew:"https://sun59-2.userapi.com/impg/-ItZhDXTxSTLIOmYpODOQBKq05WM6KnPQ2BTTw/UCUVJbejkIw.jpg?size=1280x960&quality=96&sign=4eccc31fea95d92ac19fb8f9577dfd1c&type=album",
        infNew:'22 июня 1941 года – одна из самых печальных дат в истории России – День памяти и скорби – день начала Великой Отечественной войны.\n' +
            'Участники школьного отряда всероссийского движения "Юнармия" провели митинг, посвященный Дню памяти и скорби.\n' +
            'Участники лагеря "Тайм-аут" почтили память павших минутой молчания и возложили цветы у стелы «Вам, отстоявшим весну на Земле – вечная слава», установленной в память боевого и трудового подвига выпускников и учителей военных лет.',
        id: 1
      },
        {
          imgNew:"https://sun59-1.userapi.com/impg/nP7aNkJTIiqZeW8cqcOKCXAVvbke_CRja5T1CA/KMZmCoGZcBg.jpg?size=1280x960&quality=96&sign=eea69ccc192442901781fb8997bf8124&type=album",
          infNew:'21 июня - день, посвященный Дню памяти и скорби. Ребята почтили память солдат, погибших защищая нашу Родину в годы Великой Отечественной войны.\n' +
              '23 июня отмечается Международный Олимпийский день, и сегодня в рамках трека "Орлёнок-спортсмен" орлята говорили об олимпийском движении, олимпийских видах спорта, встретились с бронзовым призёром Олимпийских игр 1980 года, учителем физической культуры Надеждой Николаевной Филипповой.\n' +
              'рассказавшая ребятам о своей спортивной карьере. Сегодня же были подведены итоги летнего фестиваля ГТО лагеря. Призёры были награждены грамотами и сладкими призами.',
          id: 2
        },
        {
          imgNew:"https://sun9-48.userapi.com/impg/Dit_19Egxx8VL4Epw1wzARIq3vJ2DfEn8DEnOA/AE_7zg3yvoI.jpg?size=1280x958&quality=96&sign=fc397705c9cfddeec7d82fa7de2cbf6f&type=album",
          infNew:'Завершилась работа пришкольных лагерей. 21июня делегация будущих юнармейцев побывала в Центре военно-патриотического воспитания г. Н. Новгорода на беседе, посвящённой Дню памяти и скорби - Дню начала Великой Отечественной войны. Далее все участники патриотического трека вместе отправились в Технический музей.\n' +
              'При подведении итогов ребята нарисовали, что им больше всего понравилось в лагере.',
          id: 3
        },
        // {
        //   imgNew: "",
        //   infNew: "20 июня ребята из лагеря \"Тайм-Аут. Время Активных\" проходили два трека: \"Орлёнок- спортсмен\" и \"Орлёнок-доброволец\". Ребята-орлята завершили комплекс оздоровительно-обучающих занятий в бассейне и поучаствовали в малых олимпийских играх, посвящённых Международному олимпийском дню, который отмечается 23 июня. А еще орлята увлечённо писали письма солдатам, которые участвуют в Специальной военной операции и ждут тёплые слова поддержки из родных мест. Своих не бросаем!",
        //   id: 4
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // },
        // {
        //   imgNew: "",
        //   infNew: "",
        //   id: 1
        // }
      ],
      blockNews1: [{
        imgNew:"https://sun59-2.userapi.com/impg/-ItZhDXTxSTLIOmYpODOQBKq05WM6KnPQ2BTTw/UCUVJbejkIw.jpg?size=1280x960&quality=96&sign=4eccc31fea95d92ac19fb8f9577dfd1c&type=album",
        infNew:'22 июня 1941 года – одна из самых печальных дат в истории России – День памяти и скорби – день начала Великой Отечественной войны.\n' +
            'Участники школьного отряда всероссийского движения "Юнармия" провели митинг, посвященный Дню памяти и скорби.\n' +
            'Участники лагеря "Тайм-аут" почтили память павших минутой молчания и возложили цветы у стелы «Вам, отстоявшим весну на Земле – вечная слава», установленной в память боевого и трудового подвига выпускников и учителей военных лет.',
        id: 1
      },
        {
          imgNew:"https://sun59-1.userapi.com/impg/nP7aNkJTIiqZeW8cqcOKCXAVvbke_CRja5T1CA/KMZmCoGZcBg.jpg?size=1280x960&quality=96&sign=eea69ccc192442901781fb8997bf8124&type=album",
          infNew:'21 июня - день, посвященный Дню памяти и скорби. Ребята почтили память солдат, погибших защищая нашу Родину в годы Великой Отечественной войны.\n' +
              '23 июня отмечается Международный Олимпийский день, и сегодня в рамках трека "Орлёнок-спортсмен" орлята говорили об олимпийском движении, олимпийских видах спорта, встретились с бронзовым призёром Олимпийских игр 1980 года, учителем физической культуры Надеждой Николаевной Филипповой,.\n' +
              'рассказавшая ребятам о своей спортивной карьере. Сегодня же были подведены итоги летнего фестиваля ГТО лагеря. Призёры были награждены грамотами и сладкими призами.',
          id: 2
        },
        // {
        //   imgNew:"https://sun9-48.userapi.com/impg/Dit_19Egxx8VL4Epw1wzARIq3vJ2DfEn8DEnOA/AE_7zg3yvoI.jpg?size=1280x958&quality=96&sign=fc397705c9cfddeec7d82fa7de2cbf6f&type=album",
        //   infNew:'Завершилась работа пришкольных лагерей. 21июня делегация будущих юнармейцев побывала в Центре военно-патриотического воспитания г. Н. Новгорода на беседе, посвящённой Дню памяти и скорби - Дню начала Великой Отечественной войны. Далее все участники патриотического трека вместе отправились в Технический музей.\n' +
        //       'При подведении итогов ребята нарисовали, что им больше всего понравилось в лагере.',
        //   id: 3
        // },
      ],
       blockTeam:[
           {
        imgTeacher: "https://sun9-43.userapi.com/impg/VZnBv-I-LO9je2UKMuLJ6OjepUP_GSkBELsjvQ/voojIlnyxlU.jpg?size=700x700&quality=96&sign=8c925f92690187404c968e087cefe09a&type=album",
        nameTeacher:'Никольская Марина Петровна',
        txtTeacher:'Начальник лагеря',
        id: 1
      },
         {
           imgTeacher: "https://sun9-30.userapi.com/impg/xlyeRywtW1g0sZn5gnE3Y6EyIoSLRN8oneIYUQ/bh4AQnVk2mE.jpg?size=350x350&quality=96&sign=2f9e70b2482750486841bfddecbfe925&type=album",
           nameTeacher:'Арсентьева Екатерина Геннадьевна',
           txtTeacher:'Воспитатель',
           id:2
         },
         {
           imgTeacher: "https://sun9-79.userapi.com/impg/Cq_nM85s1M_UkCtRZcENNDDfJBEg_ajwVG47xQ/zGrS6fkl-_c.jpg?size=350x350&quality=96&sign=1fa84441fffee82372b97a62b2c4cc5c&type=album",
           nameTeacher:'Козлова Марина Вениаминовна',
           txtTeacher:'Воспитатель',
           id: 3
         },
         {
           imgTeacher: "https://sun9-7.userapi.com/impg/de0MAtKoGNsILDPdORj8u9jopAcfRlkZQfmh9g/fD8NA_u757Y.jpg?size=680x700&quality=96&sign=0b617fbd24ae11952f876494fed46228&type=album",
           nameTeacher:'Гришина Ольга Александровна',
          txtTeacher:'Воспитатель',
           id: 4
         },
         {
           imgTeacher: "https://sun9-17.userapi.com/impg/TyIOu2VoZ8honGIv6lD-z4GC7qSbXo_PRKdeZg/OQeMFkgCF9Q.jpg?size=1280x1280&quality=96&sign=b9241752b0547709ddc5dca4b00a0bfe&type=album",
           nameTeacher:'Гусева Виктория Викторовна',
           txtTeacher:'Воспитатель',
           id: 5
         },
         {
           imgTeacher: "https://sun59-1.userapi.com/impg/tM8oXTZDDNrJqiyf2opYmFgnYH5KEd_2aS7BUw/PtZfyuKwX64.jpg?size=1280x1280&quality=96&sign=7eb881aa651dff2c6ea39ef1a3e2d6c9&type=album",
           nameTeacher:'Семенова Наталья Вячеславовна',
           txtTeacher:'Воспитатель',
           id: 6
         },
         {
           imgTeacher: "https://sun59-1.userapi.com/impg/Z0PbYADvD2xm28tKaRML95K1pCDiGhbmT1xM6Q/C6g5GMT7CDo.jpg?size=1280x1280&quality=96&sign=769e5e7872deb57fffa5df8d46bdc824&type=album",
           nameTeacher:'Кузнецова Светлана Владимировна',
           txtTeacher:'Воспитатель',
           id:7
         },
         {
           imgTeacher: "https://sun9-7.userapi.com/impg/6pb2y9SAHnJm7dvtAJMza2Ol1BgEoPVm85sUNQ/Sy5eQnZmIZo.jpg?size=340x350&quality=96&sign=16f92f9a557e04c998ed3b7ac365fddd&type=album",
           nameTeacher:'Иголкин Сергей Владимирович',
           txtTeacher:'Воспитатель',
           id: 8
         },
         {
           imgTeacher: "https://sun9-54.userapi.com/impg/qiGnqueY72ADsoYbw0z64JOsSGFi8o-VWMPbvA/VqVlsVHSjVY.jpg?size=1280x1280&quality=96&sign=cedaad05ff5ed46194ffcc7e61519b66&type=album",
           nameTeacher:'Ишимбаев Денис Кимальевич',
           txtTeacher:'Воспитатель',
           id:9
         }
      ],
      blockTeam1:[
        {
          imgTeacher: "https://sun9-43.userapi.com/impg/VZnBv-I-LO9je2UKMuLJ6OjepUP_GSkBELsjvQ/voojIlnyxlU.jpg?size=700x700&quality=96&sign=8c925f92690187404c968e087cefe09a&type=album",
          nameTeacher:'Никольская Марина Петровна',
          txtTeacher:'Начальник лагеря',
          id: 1
        },
        {
          imgTeacher: "https://sun9-30.userapi.com/impg/xlyeRywtW1g0sZn5gnE3Y6EyIoSLRN8oneIYUQ/bh4AQnVk2mE.jpg?size=350x350&quality=96&sign=2f9e70b2482750486841bfddecbfe925&type=album",
          nameTeacher:'Арсентьева Екатерина Геннадьевна',
          txtTeacher:'Воспитатель',
          id: 2
        },
        {
          imgTeacher: "https://sun9-79.userapi.com/impg/Cq_nM85s1M_UkCtRZcENNDDfJBEg_ajwVG47xQ/zGrS6fkl-_c.jpg?size=350x350&quality=96&sign=1fa84441fffee82372b97a62b2c4cc5c&type=album",
          nameTeacher:'Козлова Марина Вениаминовна',
          txtTeacher:'Воспитатель',
          id: 3
        },
        {
          imgTeacher: "https://sun9-7.userapi.com/impg/de0MAtKoGNsILDPdORj8u9jopAcfRlkZQfmh9g/fD8NA_u757Y.jpg?size=680x700&quality=96&sign=0b617fbd24ae11952f876494fed46228&type=album",
          nameTeacher:'Гришина Ольга Александровна',
          txtTeacher:'Воспитатель',
          id: 4
        },
        ]
    }
  },
methods:{
  openR(){
    this.openRegistration = !this.openRegistration;
  },
  openF(){
    this.openFoto = !this.openFoto;
  },
  openA(){
    this.openAuthorization = !this.openAuthorization;
  },
  regUser(post){
    let key = Date.now();
    let regExpSur = /[А-Я]\W+/;
    let regExpName = /[А-Я]\W*/;
    if(post.surname.match(regExpSur) && post.name.match(regExpName)){
      const userInfo = {
        login:post.login,
        password:post.password,
        surname:post.surname,
        name:post.name,
      }
      localStorage.setItem(key.toString(), JSON.stringify(userInfo));
      this.openR();
    }else{
      alert('Данные введены неверно')
    }
  },
  authoUser(user){
    let userAuto;
    for (let i=0; i<localStorage.length; i++) {
      const key = localStorage.key(i);
      const value = localStorage[key];
      let user1 = JSON.parse(value);
      if (user.login===user1.login && user.password===user1.password) {
        userAuto=user1;
        this.statusUser = !this.statusUser;
        this.objectAuthoUser ={ //Для авторизации
          name:user1.name,
          surname:user1.surname,
        }
        break;
      }
    }

    if (!userAuto) {
      alert("Пользователь не найден");
    }
    this.openAuthorization = !this.openAuthorization
  },
  funcMoveR(){
   this.blockNews.push(this.blockNews[0])
    this.blockNews.splice(0,1)
    console.log(this.blockNews)
    this.blockNews1 = this.blockNews.slice(0,2)
  },
  funcMoveL(){
    this.blockNews.unshift(this.blockNews[2])
    this.blockNews.splice(3,1)
    this.blockNews1 = this.blockNews.slice(0,2)
  },
  funcMoveRight(){
    this.blockTeam.push(this.blockTeam[0])
    this.blockTeam.splice(0,1)
    this.blockTeam1 = this.blockTeam.slice(0,4)
  },
  funcMoveLeft(){
    this.blockTeam.unshift(this.blockTeam[8])
    this.blockTeam.splice(10,1)
    this.blockTeam1 = this.blockTeam.slice(0,4)
  }

}
}
</script>

<style>
body{
  //background-image: url("https://textiledata.ru/upload/resize_cache/webp/iblock/7ea/divine_01_rapport.webp");
  //background-size: cover;
  //background-repeat: repeat;
  //background-attachment: fixed;
  background-color: #EFEFEF;
}
.container{
  width: 1600px;
}
.schol{
  width: 82%;
  margin-left: 200px;
  margin-top: 20px;
}

</style>

