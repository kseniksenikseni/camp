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
    <my-feedbacks/>
    <my-form class="myform" @create="addFeed" :statusUser="statusUser"/>
    <my-spisok :forms="forms"/>

    <my-footer/>
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
import MyForm from "@/components/MyForm.vue";
import MyFeedbacks from "@/components/MyFeedbacks.vue";
import MySpisok from "@/components/MySpisok.vue";
export default {
  components:{
    MySpisok,
    MyFeedbacks,
    MyForm,
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
      statusUser: false,
      forms: [],
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
              '23 июня отмечается Международный Олимпийский день, и сегодня в рамках трека "Орлёнок-спортсмен" орлята говорили об олимпийском движении, олимпийских видах спорта, встретились с бронзовым призёром Олимпийских игр 1980 года, учителем физической культуры Надеждой Николаевной Филипповой,\n' +
              'рассказавшая ребятам о своей спортивной карьере. Сегодня же были подведены итоги летнего фестиваля ГТО лагеря.',
          id: 2
        },
        {
          imgNew:"https://sun9-48.userapi.com/impg/Dit_19Egxx8VL4Epw1wzARIq3vJ2DfEn8DEnOA/AE_7zg3yvoI.jpg?size=1280x958&quality=96&sign=fc397705c9cfddeec7d82fa7de2cbf6f&type=album",
          infNew:'Завершилась работа пришкольных лагерей. 21июня делегация будущих юнармейцев побывала в Центре военно-патриотического воспитания г. Н. Новгорода на беседе, посвящённой Дню памяти и скорби - Дню начала Великой Отечественной войны. Далее все участники патриотического трека вместе отправились в Технический музей.\n' +
              'При подведении итогов ребята нарисовали, что им больше всего понравилось в лагере.',
          id: 3
        },
        {
          imgNew: "https://sun59-1.userapi.com/impg/wQEX20gIHmHi4bpYdyUK-hCFQ9uqPgoryldtWg/dmHrHCvgKuc.jpg?size=1280x960&quality=96&sign=6e7e9a54ea842d1712baaeb4f36841ef&type=album",
          infNew: "20 июня ребята из лагеря \"Тайм-Аут. Время Активных\" проходили два трека: \"Орлёнок- спортсмен\" и \"Орлёнок-доброволец\". Ребята-орлята завершили комплекс оздоровительно-обучающих занятий в бассейне и поучаствовали в малых олимпийских играх, посвящённых Международному олимпийском дню, который отмечается 23 июня. А еще орлята увлечённо писали письма солдатам, которые участвуют в Специальной военной операции и ждут тёплые слова поддержки из родных мест. Своих не бросаем!",
          id: 4
        },
        {
          imgNew: "https://sun59-1.userapi.com/impg/xLl4nqUTqmbHoZnEx4o40SvMMbvdfWnCxQqVTg/is_XWOiamw0.jpg?size=1280x958&quality=96&sign=4d56e897238a3fd0d0672a59ec901ed9&type=album",
          infNew: "Нас продолжают догонять фотографии из лагеря \"Тайм-аут\". Будущие юнармейцы побывали на мастер-классе по оригами в библиотеке Кольцова. Результатом работы стали разноцветные бабочки. Затем ребята отправились на поиски сокровищ капитана Флинта в ДК \"ГАЗ\". Выполняя увлекательные задания, решая головоломки, ребята справились с поисками клада.",
          id: 5
        },
        {
          imgNew: "https://sun59-2.userapi.com/impg/KwUT3lkDGEtQ9ixfJykFcWvG4dVA9c27elEpoA/SCIOjpOALi4.jpg?size=1280x960&quality=96&sign=8d74ad3f60996de205cc7bf1beb3ef71&type=album",
          infNew: "В понедельник будущие юнармейцы из лагеря \"Тайм-аут\" побывали на кинопоказе в ДК \"ГАЗ\", где посмотрели фильм \" Солдатик\".\n" +
              "Сегодня в библиотеке Бажова для ребят прошел краеведческий квест, а после обеда их ждала увлекательная игра \"Следопыт\".",
          id: 6
        },
        {
          imgNew: "https://sun59-1.userapi.com/impg/f1jRblftGxwf_GsSvp0WJw2I4xaRwfAdGXOMWQ/hl7QP0si1M8.jpg?size=1280x964&quality=96&sign=51214c9c104fb716d508962e7c38fd86&type=album",
          infNew: "19 июня в лагере \"Тайм-аут. Время Активных\" проходил трек \"Орлёнок-хранитель\". Ребята говорили о нижегородцах, которые прославили родной город в разные эпохи и посетили интерактивную экскурсию \"В гостях у древнего Кремля\", на которой узнали о тайнах и легендах крепостного сооружения. Также ребята занимались в объединениях дополнительного образования под руководством педагогов Центра детского творчества Ленинского района. День прошел интересно и познавательно!",
          id: 7
        },
        {
          imgNew: "https://sun9-17.userapi.com/impg/BbzV1r_KuQtlRsyhyDHyRPoi0eWtvq_2cEkKog/JWLphPc67vs.jpg?size=1280x960&quality=96&sign=dcd55d3a971645be317194621b2dfa47&type=album",
          infNew: "16 июня в лагере \"Тайм-Аут. Время активных\" проходил трек \"Орлёнок-мастер\". Ребята, разделившись на три возрастные группы, осваивали новые умения и приобретали новые знания - учились создавать мультфильмы на мастер-классе мультакадемии, сдавали нормативы на фестивале ГТО, узнавали о тонкостях промыслов родного края на интерактивном занятии \"Вечные ремёсла земли нижегородской\", приуроченном к Дню народных художественных промыслов. Завершился день занятиями объединений дополнительного образования под руководством педагогов Центра детского творчества Ленинского района. ",
          id: 8
        },
        {
          imgNew: "https://sun9-41.userapi.com/impg/Dof_82Myiox2ivQr17zh4UHEmVMI-iAncZy9Lw/wDnAV76QQR8.jpg?size=1280x960&quality=96&sign=e85f611968f4cdef125156a56598a68a&type=album",
          infNew: "15 июня ребята из лагеря \"Тайм-аут. Время активных\" проходили трек \"Орленок-лидер\". Орлята приняли участие лидерских играх \"Гонка за лидером\". А о тайнах космического пространства ребята узнали под куполом планетария. В четверг - уже традиционно - поход в бассейн, а значит, что сегодня мы укрепляли здоровье и повышали настроение.",
          id: 9
        },
        {
          imgNew: "https://sun9-64.userapi.com/impg/kbLJXwRqBYH9JtJJDxuKASw7vNYaU9eWSpV0pA/CRSCIfDoFjE.jpg?size=1280x961&quality=96&sign=cda39bddf1395893229e5bb65ac16a97&type=album",
          infNew: "15 июня участники патриотического трека лагеря \"Тайм-аут. Время активных\" проявили свои творческие способности в формате стрит-арт на асфальте на тему \"Я живу в России\". А во второй половине дня сотрудница библиотеки им. Бажова провела для ребят экскурсию по микрорайону Красная Этна.",
          id: 10
        },
        {
          imgNew: "https://sun9-50.userapi.com/impg/pgqMRKagfIUwPOXxA1EXL0J1nBA1EK7-ncLtxw/do0joq4z4To.jpg?size=1280x960&quality=96&sign=859c090b9ccbfc3da704d8d28c321b08&type=album",
          infNew: "14 июня ребята из лагеря \"Тайм-Аут. Время активных\" проходили трек \"Орлёнок- эрудит\". Много важной и нужной информации узнали ребята в Vеждународный день донора крови о людях, помогающих спасать жизни. Ребята пообщались с учителем Викторией Викторовной Гусевой, которая сама является донором. В Нижегородской филармонии ребята с интересом слушали \"Сказки Венского леса\". С педагогами дополнительного образования Центра детского творчества Ленинского района ребята продолжали творить и расширять свой кругозор.",
          id: 11
        },
        {
          imgNew: "https://sun9-51.userapi.com/impg/Tp_zuyPkkf__ueYBLaOF3Dp4RxIiM20mW1yhPA/8JhNmDh7jso.jpg?size=1280x854&quality=96&sign=0a915f42e91db416d8a2d44cba629162&type=album",
          infNew: "Еще один насыщенный день лагеря труда и отдыха \"Тайм-аут. Время творческих\". Профессиональные пробы по треку \"Юный электрик\", игра \"Бампербол\" и квест \"12 записок\". Также ребята смогли проявить свои способности в игре \"Будь в движении\", направленной на закреплении представлений о направлениях деятельности и ценностях РДДМ \"Движение первых\"",
          id: 12
        },
        {
          imgNew: "https://sun59-2.userapi.com/impg/pMgvWnn9esilGfR6jQe-BZ6gviqf_PH2-1gV5g/52VxBjpxBqw.jpg?size=1280x960&quality=96&sign=284d814567807444dc223b992f648ddc&type=album",
          infNew: "Сегодня участники патриотического трека лагеря \"Тайм-аут. Время активных\" посетили Нижегородскую филармония, где посмотрели спектакль \"Сказки Венского леса\".",
          id: 13
        },
        {
          imgNew: "https://sun9-74.userapi.com/impg/l8vPeMIi9FGyBb0IbrDF6OFueLZX-PmcrFXOyg/tn5lLekVRkg.jpg?size=1280x854&quality=96&sign=46c7051cf645e60d288ce50d34edb651&type=album",
          infNew: "Участники лагеря труда и отдыха \"Тайм-аут. Время творческих\" продолжают профессиональные пробы. Участники отправились на экскурсию в полк патрульно - постовой службы полиции Управления МВД России по Нижнему Новгороду. Обучающиеся узнали, как организована охрана общественного порядка, посетили музей полка патрульно - постовой службы, где узнали об истоках формирования подразделения, познакомились с тактическими приемами, которые сотрудники полиции используют в охране общественного порядка. Осмотрели состоящие на вооружении современные специальные средств, а узнали о том, как работает кинологическая служба.",
          id: 14
        },
        {
          imgNew: "https://sun9-79.userapi.com/impg/TGWCcBOdQbijBi8DtVFTrCJ7rt7J_WVtwWK06g/-kDpjioKO_U.jpg?size=1280x854&quality=95&sign=2db1541008300112b960481034bfb1bc&type=album",
          infNew: "Активисты школьного отделения Российского движения детей и молодежи \"Движение Первых\" организовали для участников лагеря труда и отдыха «Тайм-аут. Время творческих» игру «Будь в движении». Игра была направлена на закрепление представлений о направлениях деятельности и ценностях РДДМ «Движение Первых».",
          id: 15
        },
        {
          imgNew: "https://sun9-43.userapi.com/impg/s4MgjDi9Vz25hSL2b0SnFJqnhoZNpH0yE9RDdg/oaUBM7rzOEM.jpg?size=1280x960&quality=96&sign=a2a854b39e635d3f3520c1fbeaf156c3&type=album",
          infNew: "13 июня продолжил работу лагерь с дневным пребыванием \"Тайм-АУТ. Время активных\". Сегодня юные орлята проходили трек \"Орленок-эрудит\". Летом школа не заканчивается, просто обучение проходит в другой форме. Участники лагеря проявили свои знания и смекалку в КВИЗе \"Знатоки лагеря\", а самое интересное ждало ребят на встрече с артистами отделения научных открытий ТЮЗа. Ребята в занимательной форме узнавали необычное об обычном и знакомились с чудесами науки.",
          id: 16
        },
        {
          imgNew: "https://sun9-80.userapi.com/impg/3zj0AO4s33L8cmeBLxj0slXSQwgKyBeePTBWAA/YMbxdAv6q4M.jpg?size=1280x958&quality=96&sign=0d519ffbabe4a288478c64bf042a0542&type=album",
          infNew: "13 июня Участники патриотического трека лагеря \"Тайм-аут\" приняли участие в игре \"Бампербол\". Во второй половине дня специалисты библиотеки им. Бажова провели для ребят патриотическое мероприятие \"Россия в сердце навсегда\".",
          id: 17
        },
        {
          imgNew: "https://sun9-59.userapi.com/impg/dj5rsn1rRnrO2uKR94FRHVMIepzuCNQrSb_VWA/w4mKJmKHJII.jpg?size=1280x960&quality=96&sign=8940969c6dccb7ecf9e2c248f4f3612e&type=album",
          infNew: "9 июня ребята из лагеря \"Тайм-аут. Время активных\" провели историческую пятиминутку \"Я горжусь своей страной\", посвященную Дню России. В театре юного зрителя ребята посмотрели поучительный спектакль \"В стране невыученных уроков\". Сегодня продолжились занятия в объединениях дополнительного образования \"Городецкая палитра\", \"Зеленая лаборатория\", \"Скетчинг. Школа креатива.\" и \"Азбука творчества\".",
          id: 18
        },
        {
          imgNew: "https://sun9-13.userapi.com/impg/_lg_-GRG7oHM9WTdq8-AOiggHx7175Sz6pTzjQ/WFHTnmOpxkk.jpg?size=1280x958&quality=96&sign=7714419c656672efd9c0db1d6c69390c&type=album",
          infNew: "Будущие юнармейцы, участники патриотического трека лагеря \"Тайм-аут\" посетили Театр юного зрителя, где посмотрели спектакль \"В стране невыученных уроков\".",
          id: 19
        },
        {
          imgNew: "https://sun9-50.userapi.com/impg/Ncf_-Ni55XfKViKjwCukfty6IllyxCimXdUkkw/jx9UBuDL4nU.jpg?size=1280x854&quality=96&sign=01202454108677be7a6e250868cd4997&type=album",
          infNew: "8 июня воспитанники лагеря труда и отдыха \"Тайм-аут. Время творческих\" прошли приключенческий квест \"Сокровища капитана Флинта\", знакомились с профессией \"Археолог\" и занимались поисковыми работами, а также вспоминали историю Нижнего Новгорода, участвуя в квизе \"Мой Нижний\".",
          id: 20
        },
        {
          imgNew: "https://sun9-45.userapi.com/impg/KVkQ_PEEFhB1wsUz5uFDfrmZxiD-jkuIskuCfg/1gPBbPeF1gY.jpg?size=1280x854&quality=96&sign=211d4ddb3f8a77428c9b3ee1100de413&type=album",
          infNew: "Участники лагеря труда и отдыха \"Тайм-аут. Время творческих\" совершили пешую прогулку по маршруту \"ул. Большая Покровская - набережная Федоровского\". Во время экскурсии ребята узнали много новых исторических фактов про город. Также в лагере прошел турнир по дартсу.",
          id: 21
        },
        {
          imgNew: "https://sun9-29.userapi.com/impg/B7wR-HD29KTYkJUgGRhpe0MzCDc0bkssJoxj1A/Rzk-h3TrZb4.jpg?size=1280x961&quality=96&sign=0f5b6edb7e7c558af438f0eb2d30e294&type=album",
          infNew: "Фестиваль спортивных событий, посвященный 100-летию Министерства спорта РФ, прошёл сегодня в лагере \"Тайм Аут. Время Успешных\". Будущие юнармейцы посетили бассейн, проверили свою меткость в турнире по дартсу (девчонки оказались лучшими снайперами) и сыграли партию игр в пионербол.",
          id: 22
        },
        {
          imgNew: "https://sun9-42.userapi.com/impg/-Mips_8UIMnFyAljzX4C2Bi2Qv8uV59J3xoasA/uZwyEnQHZO0.jpg?size=1280x960&quality=96&sign=4993adcc9914d432243da5e9cf9c4cf6&type=album",
          infNew: "Участники школьного лагеря \"Тайм-аут. Время творческих\" продолжили профессиональные пробы и поучаствовали в работе школьного учебного раскопа. Открывая для себя профессию \"Археолог\" ребята познакомились с азами поисковой археологии - проследили историю солдатских медальонов от самодельных образцов из гильз до современных образцов. Практическим заданием сдал поиск информации о бойце с последующим заполнением красноармейской книжки.",
          id: 23
        },
        {
          imgNew: "https://sun9-22.userapi.com/impg/cOlutR202ETNSYDtbNLllM-JL0xsl71BJcxcEQ/qPm_fTH2Tgc.jpg?size=1280x960&quality=96&sign=c93f26c55bf54ca7d1ad630b1a01499e&type=album",
          infNew: "8 июня - День океанов. В рамках трека \"Орленок-эколог\" участники лагеря \"Тайм-Аут. Время активных\" стали активными участниками познавательной программы \"В гости к океану\". Занятие в бассейне способствовало укреплению здоровья. А еще в гостях у ребят сегодня побывали артисты \"Театра на Счастливой\" с интерактивным спектаклем \"Правило трёх НЕ\". Спектакль помог юным зрителям с помощью героев сказки закрепить правила дорожного движения. День прошел интересно и с пользой.",
          id: 24
        },
        {
          imgNew: "https://sun9-79.userapi.com/impg/ZPzeCvWNGFbLVUL7Dz1tvzTtcCm5Y2NJJK7s-w/Tygh2MgGZxs.jpg?size=1280x960&quality=96&sign=727f810058f61d718c25bd0a4e9da43a&type=album",
          infNew: "7 июня участники патриотического трека лагеря \"Тайм-аут. Время активных\" приняли участие в исторической викторине, а затем отправились в мультимедийный исторический парк \"Россия - моя история\", чтобы пройтись по страницам истории Нижегородского края. После обеда будущие юнармейцы продолжили осваивать искусство флешмоба.",
          id: 25
        },
        {
          imgNew: "https://sun9-18.userapi.com/impg/SZfkW7UvxXhPQyTOo0i7-5UVLSTwIFN3y7vbRQ/SIDhewQkP8s.jpg?size=1280x960&quality=96&sign=f1eaed332ac9a53d4f3e5e95be9a35ad&type=album",
          infNew: "Участники школьных лагерей включились во Всероссийскую акцию «Окна России».",
          id: 26
        },
        {
          imgNew: "https://sun9-6.userapi.com/impg/zVUkOxs6rEb5teefKNJcmk7E8SiyCdaGrForCw/KyAWlzSWAfg.jpg?size=1280x960&quality=96&sign=fa9864c086270408d9a3f64533be63fb&type=album",
          infNew: "7 июня ребята из лагеря \"Тайм-аут. Время активных\" были активными участниками фестиваля спортивных игр, который для них провела Светлана Дмитриевна Никольская. Беседу \"Люди огненной профессии провела для ребят Светлана Владимировна Кузнецова. Продолжили разговор о безопасности обращения с огнем, умении защитить себя и свой дом на мероприятиях в библиотеке им. Кольцова, в пожарно-спасательной части №8 и Центре противопожарной пропаганды и общественных связей МЧС России.",
          id: 27
        },
        {
          imgNew: "https://sun9-77.userapi.com/impg/9z3-h9F4jjlSOJwzcwU_C6ntxoPFlTMMG4rhTA/D2lkoCv0YqI.jpg?size=1280x854&quality=96&sign=f3f83ac36dacdb33519fbaed1bd54d30&type=album",
          infNew: "6 июня воспитанники лагеря труда и отдыха \"Тайм-аут. Время творческих\" посетили музей истории завода \"Красное Сормово\", а также продолжили участвовать в занятиях по профессиональному самоопределению. Также сотрудниками библиотеки им. П.П. Бажова был проведен исторический КВИЗ.",
          id: 28
        },
        {
          imgNew: "https://sun9-4.userapi.com/impg/zjodq6uniHsavH-t87zy37hX89bkky1cYuZNbA/54k0HDubz64.jpg?size=1280x961&quality=96&sign=edf87d307805b827e22ac6064d159ccd&type=album",
          infNew: "В День русского языка участники патриотического трека лагеря \"Тайм-аут. Время активных\" посетили библиотеку имени Бажова. Мероприятие было приурочено ко дню рождения А.С. Пушкина. В режиме дня будущих юнармейцев находится место и спорту.",
          id: 29
        },
        {
          imgNew: "https://sun9-32.userapi.com/impg/Sh7u25UKAJT89yYDanjaRkakXLqMNo3fI_Dvlg/4gKm6tnQc04.jpg?size=1280x960&quality=96&sign=5b474c620e3214a12047232db72ef59c&type=album",
          infNew: "6 июня - Пушкинский день России и День русского языка. Творчество А.С. Пушкина, а в особенности его сказки, учат любить Россию, понимать поэзию своей страны, узнавать богатый и милый сердцу русский язык, как научила понимать его самого поэта няня А. Р. Матвеева. И сегодня ребята узнали о том, какую роль сыграла Нижегородская губерния в творчестве Пушкина, проявили свои знания в викторине \"Мир сказок Пушкина\" и окунулись в историческую атмосферу времен А.С. Пушкина вместе с работниками музея им. Добролюбова. Ребята выполнили замечательные коллажи и написали письма в стилистике XIX века.",
          id: 30
        },
        {
          imgNew: "https://sun9-61.userapi.com/impg/iZD5n0AjfbrPwzQ0Fou7eO7r_gwAmdmIn8hnUA/ieYR7as4FRQ.jpg?size=1280x958&quality=96&sign=5b12ee3962f587f0058690c36ceeba95&type=album",
          infNew: "5 июня участники патриотического трека лагеря \"Тайм-аут. Время активных\" отправились в историческую часть Нижнего Новгорода. Будущие юнармейцы познакомились с архитектурой и историей родного города.",
          id: 31
        },
        {
          imgNew: "https://sun9-5.userapi.com/impg/cL3koRu3US40RYbrZsZIpIUKzrrHIstgI9l7mA/wTTlXnVUsIU.jpg?size=1280x960&quality=96&sign=280e8dfadc907f193ae0d4b412e5e136&type=album",
          infNew: "Занятие по основам начальной военной подготовки провел для участников лагеря труда и отдыха \"Тайм-аут. Время творческих\" советник по воспитанию Даниил Андреевич Васин.\n" +
              "Участники лагеря актуализировали знания по разборке и сборке автомата Калашникова и пистолета Макарова, попробовали свои силы в работе с веревками и страховкой, познакомились с основами альпинистской подготовки на школьном учебном скалодроме.",
          id: 32
        },
        {
          imgNew: "https://sun9-70.userapi.com/impg/WOp64YQkhbC8CmqYAXA1xcfGXMR_NZ5EDLkcTA/NnsnCt-JZVM.jpg?size=1280x961&quality=96&sign=fe15f0c8f458390678a22e471b29d945&type=album",
          infNew: "5 июня продолжил свою работу лагерь с дневным пребыванием \"Тайм-аут. Время активных\". В День эколога ребята познакомились с международной детско-юношеской премией \"Экология для каждого\" и многие захотели принять участие в конкурсном отборе. Ребята посетили спектакль \"Пеппи - Длинный чулок\" детской театральной студии \"Маска\" в Центре детского творчества Ленинского района и продолжили занятия в объединениях дополнительного образования \"Городецкая палитра\", \"Зеленая лаборатория\", \"Скетчинг. Школа креатива.\" и \"Азбука творчества\". ",
          id: 33
        },
        {
          imgNew: "https://sun9-47.userapi.com/impg/j8zJsDIeSTYTzKdY3_PdWxHSKFKf042dG_k4kg/U9cPPuHjD-M.jpg?size=1280x960&quality=96&sign=1eb2f8e41ef5f9b52223577c3ea5ce84&type=album",
          infNew: "2 июня в лагере \"Тайм-аут. Время Активных\". Ребята стали активными участниками культурно-развлекательной программы, посвященной Дню защиты детей, которая была организована в Дворце культуры ГАЗ, а затем прокатились на аттракционах в Автозаводском парке. В творческих мастерских, организованных Центром детского творчества Ленинского района, под руководством педагогов дополнительного образования ребята творили в объединениях \"Городецкая палитра\", \"Зеленая лаборатория\", \"Скетчинг. Школа креатива.\" и \"Азбука творчества\".",
          id: 34
        },
        {
          imgNew: "https://sun9-56.userapi.com/impg/4PT8Zxwf7IiA8fxmxiLPT-Hp8vbAnyh5XDem1Q/sif8-PKV2f8.jpg?size=1280x961&quality=96&sign=b45806e12a967acef345c9d43698895d&type=album",
          infNew: "2 июня в лагере труда и отдыха \"Тайм-аут. Время творческих\" прошли профессиональные пробы по треку \"Сити-фермерство\". Также участники смены посетили музей истории завода \"Сокол\".",
          id: 35
        },
        {
          imgNew: "https://sun9-79.userapi.com/impg/9iUdFl2_vD8JvCDSoef0vRfQkWPj-7nlQR4jkA/Wgintu2BpxU.jpg?size=1280x960&quality=96&sign=fbc0b47815e3a10c29a8918784e590a1&type=album",
          infNew: "Первые дни в лагере \"Тайм-аут\" для участников патриотического трека проходят активно: будущие юнармейцы побывали в библиотеке Кольцова, стали участниками игр на свежем воздухе, посетили бассейн. Сегодня участники смены посетили музей \"Нижегородская радиолаборатория\", а также побывали на занятии с преподавателем Центра детского творчества, где обучались искусству флешмоба. А еще у ребят появилась возможность попробовать себя в роли юных натуралистов: участники смены высадили семена бархатцев.",
          id: 36
        },
        {
          imgNew: "https://sun9-52.userapi.com/impg/LAgLIKNyVyq6ptkyE0RnpYUPFNVJT51S2SfK-A/tGKQtVcfVso.jpg?size=1280x960&quality=95&sign=9dfc6f1fc48f5fe9cb067d4f6daa687f&type=album",
          infNew: "Первый день смены в лагере труда и отдыха \"Тайм-аут. Время творческих\". Полет нормальный!..",
          id: 37
        },
        {
          imgNew: "https://sun9-16.userapi.com/impg/3Qh3EnMbSvyexgnifG3vBmorIiSK1yB1DCZ9UA/doYlOjAXaes.jpg?size=1280x960&quality=95&sign=a0b5d6eafe477edcf39faa5555a22470&type=album",
          infNew: "1 июня в МАУ «Парк Дубки» прошел  «Фестиваль детства-2023». В программу были включены гала-концерт, работа зоны спортивных и настольных игр, творческие мастер-классы, игра РДДМ «Движение первых» «Будь в движении».\n" +
              "Площадку \"Юнармейский дозор\" провели участники школьного отделения всероссийского движения \"Юнармия\" под руководством советника директора по воспитанию Даниила Андреевича Васина. Юнармейцы предложили участникам фестиваля попробовать свои силы в разборке-сборке АК-74, пистолета Макарова, снаряжении магазина патронами, установке палатки и метании спасательного конца Александрова.",
          id: 38
        },
        {
          imgNew: "https://sun9-40.userapi.com/impg/V6sqjZ_BO7ACRwkmW4ZlOXhP0IxGWJEMVV3uxA/q2quMNM-wfQ.jpg?size=1280x960&quality=96&sign=4c603ffbcac18b19dd272ef4fa12a93b&type=album",
          infNew: "1 июня началась летняя смена в пришкольном лагере \"Тайм-аут\". Старт смене был дан на торжественной линейке, где с приветственным словом к ребятам обратились директор школы Борис Владимирович Котельников и начальник лагеря Марина Петровна Никольская. 1 июня воспитанники лагеря \"Тайм-аут. Время Активных\" посетили бассейн и стали участниками шоу гигантских мыльных пузырей.",
          id: 39
        },
        {
          imgNew: "https://sun9-72.userapi.com/impg/hxb-PIT7foAgaFR-p6m1zKSevkdtIHqByNDteA/CUmDZRT3n_I.jpg?size=1280x960&quality=96&sign=7a76c9b24a6bbb901b01eae952c7e7cc&type=album",
          infNew: "1 июня, в День защиты детей, стартовала работа школьного лагеря-комплекса \"Тайм-аут\". Команда педагогов подготовила интересную программу, в которой нашли отражение проектные линии Российского движения детей и молодежи, традиционные дела школы, познавательные мастер-классы и активитеты.\n" +
              "Сегодняшний день начался с церемонии поднятия государственного флага Российской Федерации.\n" +
              "День защиты детей, отмечающийся в первый день лета, напоминает взрослым, что детство должно быть безопасным, интересным и насыщенным яркими образовательными событиями.",
          id: 40
        }
      ],
      blockNews1: [
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
              '23 июня отмечается Международный Олимпийский день, и сегодня в рамках трека "Орлёнок-спортсмен" орлята говорили об олимпийском движении, олимпийских видах спорта, встретились с бронзовым призёром Олимпийских игр 1980 года, учителем физической культуры Надеждой Николаевной Филипповой,.\n' +
              'рассказавшая ребятам о своей спортивной карьере. Сегодня же были подведены итоги летнего фестиваля ГТО лагеря.',
          id: 2
        }
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
           txtTeacher:'  Воспитатель',
           id:2
         },
         {
           imgTeacher: "https://sun9-7.userapi.com/impg/de0MAtKoGNsILDPdORj8u9jopAcfRlkZQfmh9g/fD8NA_u757Y.jpg?size=680x700&quality=96&sign=0b617fbd24ae11952f876494fed46228&type=album",
           nameTeacher:'Гришина Ольга Александровна',
           txtTeacher:'  Воспитатель',
           id: 3
         },
         {
           imgTeacher: "https://sun9-79.userapi.com/impg/Cq_nM85s1M_UkCtRZcENNDDfJBEg_ajwVG47xQ/zGrS6fkl-_c.jpg?size=350x350&quality=96&sign=1fa84441fffee82372b97a62b2c4cc5c&type=album",
           nameTeacher:'Козлова Марина Вениаминовна',
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
          txtTeacher:'  Воспитатель',
          id: 2
        },
        {
          imgTeacher: "https://sun9-7.userapi.com/impg/de0MAtKoGNsILDPdORj8u9jopAcfRlkZQfmh9g/fD8NA_u757Y.jpg?size=680x700&quality=96&sign=0b617fbd24ae11952f876494fed46228&type=album",
          nameTeacher:'Гришина Ольга Александровна',
          txtTeacher:'  Воспитатель',
          id: 3
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
      alert("Пользователь  найден");
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
    this.blockNews.unshift(this.blockNews[39])
    this.blockNews.splice(41,1)
    this.blockNews1 = this.blockNews.slice(0,2)
  },
  funcMoveRight(){
    this.blockTeam.push(this.blockTeam[0])
    this.blockTeam.splice(0,1)
    this.blockTeam1 = this.blockTeam.slice(0,3)
  },
  funcMoveLeft(){
    this.blockTeam.unshift(this.blockTeam[8])
    this.blockTeam.splice(10,1)
    this.blockTeam1 = this.blockTeam.slice(0,3)
  },
  addFeed(form){
    this.forms.push(form)
    console.log(form)
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
  font-family: Arial;
}
.container{
  width: 1600px;
}
.schol{
  width: 82%;
  margin-left: 200px;
  margin-top: 20px;
}
.myform{
  margin-top: -100px;
  margin-left: 300px;
}
</style>

