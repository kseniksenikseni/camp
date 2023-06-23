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
  <img class="schol" src="./assets/Groups.png" alt="">
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
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // }, {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        // {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // }, {
        //   imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
        //   infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
        //   id: 2
        // },
        //

        {
        imgNew:"https://sun59-1.userapi.com/impg/PiZAWDWn4mFF1xwXmfXvLaRJa-nIKY-9u82mlw/NxETEA4ivXY.jpg?size=960x960&quality=96&sign=2c98c70040e83f96f4f0b23e5137a033&type=album",
        infNew:'7 июня ребята из лагеря "Тайм-аут"',
        id: 1
      },
        {
          imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
          infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
          id: 2
        },
        {
          imgNew:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          infNew:'В День русского языка участники патриотического трека лагеря "Тайм-аут."',
          id: 3
        },
        {
          imgNew:"https://sun9-59.userapi.com/impg/RbpsKlTRjncCdurdh9qVn61jljBITg825cqPgw/JX0GMpYVSH0.jpg?size=960x960&quality=96&sign=ce8c173c4b9a2c8d2ad878fa280524f1&type=album",
          infNew:'6 июня - Пушкинский день России и День русского языка.',
          id: 4
        }
      ],
      blockNews1: [{
        imgNew:"https://sun59-1.userapi.com/impg/PiZAWDWn4mFF1xwXmfXvLaRJa-nIKY-9u82mlw/NxETEA4ivXY.jpg?size=960x960&quality=96&sign=2c98c70040e83f96f4f0b23e5137a033&type=album",
        infNew:'7 июня ребята из лагеря "Тайм-аут"',
        id: 1
      },
        {
          imgNew:"https://sun9-42.userapi.com/impg/LxeZhk4o9x6SYlXhd1iUdgZlLUaqewN-tbs9Uw/16cPFgFYkfA.jpg?size=854x853&quality=96&sign=3a6cc0b37db4ceb114e9fb411ff8f0e2&type=album",
          infNew:'6 июня воспитанники лагеря труда и отдыха "Тайм-аут."',
          id: 2
        },
        {
          imgNew:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          infNew:'В День русского языка участники патриотического трека лагеря "Тайм-аут."',
          id: 3
        },
        {
          imgNew:"https://sun9-59.userapi.com/impg/RbpsKlTRjncCdurdh9qVn61jljBITg825cqPgw/JX0GMpYVSH0.jpg?size=960x960&quality=96&sign=ce8c173c4b9a2c8d2ad878fa280524f1&type=album",
          infNew:'6 июня - Пушкинский день России и День русского языка.',
          id: 4
        }
      ],
       blockTeam:[
           {
        imgTeacher: "https://sun9-48.userapi.com/impg/9BwCly2q70iLI1BTOvWyEb1DnT7IptkM80ZLhQ/8058OvsX_Lg.jpg?size=350x350&quality=96&sign=5997104d5db5c968825dabf182f9640a&type=album",
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
           nameTeacher:'Козлова',
           txtTeacher:'Воспитатель',
           id: 3
         },
         {
           imgTeacher: "https://sun9-20.userapi.com/impg/o5kH4G3V5XRhTeR1_N9e9cU2itTxDfzE-AD2cA/_-tdGaeXNy4.jpg?size=340x350&quality=96&sign=aeb6e4aea309dafb8459a4c9fab4464c&type=album",
           nameTeacher:'Гришина Ольга Александровна',
          txtTeacher:'Воспитатель',
           id: 4
         },
         {
           imgTeacher: "https://sun59-2.userapi.com/impg/3MpJdkQgmedjIjm9NfNPudDaHmv1YNP4WVSdhQ/KN74igtpnDY.jpg?size=350x350&quality=96&sign=e63721393ce3c22300f52a73fdb8f1a2&type=album",
           nameTeacher:'Гусева Виктория Викторовна',
           txtTeacher:'Воспитатель',
           id: 5
         },
         {
           imgTeacher: "https://sun9-73.userapi.com/impg/QRX1hOi0i2yJo6JU7i9HyAtnx_BJ387bXQcTlA/Vx8VNo6x-RE.jpg?size=350x350&quality=96&sign=e1876433118f4c66be339540aa00eb6c&type=album",
           nameTeacher:'Семенова Наталья Вячеславовна',
           txtTeacher:'Воспитатель',
           id: 6
         },
         {
           imgTeacher: "https://sun59-1.userapi.com/impg/zRmETO5i48X3RWiuxy1lt93552nF-OsLFlKw2A/31-zjTg040Q.jpg?size=350x350&quality=96&sign=7d1c467a5ade358f962c1ec5e28a92f1&type=album",
           nameTeacher:'Кузнецова Светлана Владимировна',
           txtTeacher:'Воспитатель',
           id:7
         },
         {
           imgTeacher: "https://sun59-1.userapi.com/impg/4A0l5YCvjCpkUvDgPxSoaq7xzrqu1rAdRWqGyQ/CNEg27UimZw.jpg?size=350x350&quality=96&sign=32c739dea3a8d23df2423fec6e877166&type=album",
           nameTeacher:'Иголкин Сергей Владимирович',
           txtTeacher:'Воспитатель',
           id: 8
         },
         {
           imgTeacher: "https://sun9-24.userapi.com/impg/17kWPPYDCkL8bW7UO_yiAl6Gns85KfkOqeE0oA/4VtWzRc_7k8.jpg?size=350x350&quality=96&sign=1af16aafb03295351118dcd57c9bc32b&type=album",
           nameTeacher:'Ишимбаев Денис Кимальевич',
           txtTeacher:'Воспитатель',
           id:9
         }
      ],
      blockTeam1:[
        {
          imgTeacher: "https://sun9-48.userapi.com/impg/9BwCly2q70iLI1BTOvWyEb1DnT7IptkM80ZLhQ/8058OvsX_Lg.jpg?size=350x350&quality=96&sign=5997104d5db5c968825dabf182f9640a&type=album",
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
          imgTeacher: "https://sun9-20.userapi.com/impg/o5kH4G3V5XRhTeR1_N9e9cU2itTxDfzE-AD2cA/_-tdGaeXNy4.jpg?size=340x350&quality=96&sign=aeb6e4aea309dafb8459a4c9fab4464c&type=album",
          nameTeacher:'Гришина Ольга Александровна',
          txtTeacher:'Воспитатель',
          id: 4
        },
        ],
      blockImages:[
        {
        imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 1
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 2
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 3
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 4
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 5
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 6
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 7
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 8
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 9
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 10
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 11
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 12
        },
        {
          imgImages:"https://sun9-70.userapi.com/impg/rBeIDiTryxGi5jt14loT-HqsTpnLqdsF4Tt1Ow/COjujNnOjb8.jpg?size=485x485&quality=96&sign=3939d0dc50ee5f1f0d755ae83098716a&type=album",
          id: 13
        }

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
    this.blockNews1 = this.blockNews.slice(0,4)
  },
  funcMoveL(){
    this.blockNews.unshift(this.blockNews[3])
    this.blockNews.splice(5,1)
    this.blockNews1 = this.blockNews.slice(0,4)
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

