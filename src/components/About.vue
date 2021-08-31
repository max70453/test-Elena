<template>
  <div class="reviews" >
    <h2 class="title">Отзывы о Барселоне</h2>
    <v-slide-group v-model="model" prev-icon=""
      next-icon="" center-active>
      <v-slide-item v-for="(review, i) in reviews" :key="i" v-slot="{ toggle }">
        <v-card class="review-item"
          tile
          flat
          color="#F9F7F2"
          height="410"
          width="300"
          @click="toggle"
        >
        <div class="inner">
        <header>
          <v-avatar size="30">
            <img
              alt="user"
              :src="require(`../assets/avatars/${review.avatar}`)">
          </v-avatar>
          <span class="name"> {{review.name}}</span>
        </header>
        <div class="content">
          <div class="subtitle">
            <span class="city-name">{{review.city}}</span><span> &mdash; О городе:</span>
          </div>
          <p>{{review.review}}</p>
          <div class="mt-3">
            <v-avatar size="50" tile
            v-for="(img, i) in review.images"
            :key="i"
            class="mr-2"
            :class="{last : i === (review.images.length-1)}">
            <img
              alt="img"
              :src="require(`../assets/${img.src}`)"
              @click.stop="zoomIn(img.src)">
          </v-avatar>
          </div>
        </div>
        <footer>
          <span class="small-text">{{review.date}}</span>
          <span class="small-text"> {{review.comments}} комментари{{LastSymbol(review.comments)}}</span>
          <span class="small-text">{{review.likes}}</span>
        </footer>
        </div>
        </v-card>
      </v-slide-item>
    </v-slide-group>
    <button class="all-reviews"> Все отзывы</button>
    <v-dialog
      v-model="popup"
      max-width="290">
      <v-card class="pa-5 text-center" tile flat color="#F9F7F2">
         <img alt="img" :src="require(`../assets/${this.url}`)">
         <div class="text-center">
           <v-btn small @click="popup = false" color="#FF4641" outlined>Закрыть</v-btn></div>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
export default {
  name: "About",
  data: () => ({
    popup: false,
    url: "logo.png",
    model: null,
    reviews: [
      {
        name: 'Наталия Полянская',
        avatar: 'avatar1.png',
        city: 'Барселона',
        review: 'Барселона – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...',
        images: [ {src: 'preview1.png'}, {src: 'preview2.png'}, {src: 'preview3.png'}, {src: 'preview3.png'}],
        date: 'около 1 года назад',
        comments: 9,
        likes: 9,
      },
      {
        name: 'Elena Bulgakova',
        avatar: 'avatar1.png',
        city: 'Барселона',
        review: 'Барселона – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...',
        images: [ {src: 'preview1.png'}, {src: 'preview2.png'}, {src: 'preview3.png'}, {src: 'preview3.png'}],
        date: '5 месяцев назад',
        comments: 3,
        likes: 7,
      },
      {
        name: 'Наталия Полянская',
        avatar: 'avatar1.png',
        city: 'Барселона',
        review: 'Плюсы города: весь город одни плюсы! Минусы города: не видела. В наш марафон по Европе не вписалось 2 испанских города от усталости - решили остаток путешествия провести в Барселоне ...',
        images: [ {src: 'preview1.png'}, {src: 'preview2.png'}, {src: 'preview3.png'}, {src: 'preview3.png'}],
        date: 'около 1 года назад',
        comments: 1,
        likes: 1,
      },
      {
        name: 'Elena Bulgakova',
        avatar: 'avatar1.png',
        city: 'Барселона',
        review: 'Барселона – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...',
        images: [ {src: 'preview1.png'}, {src: 'preview2.png'}, {src: 'preview3.png'}, {src: 'preview3.png'}],
        date: '5 месяцев назад',
        comments: 3,
        likes: 7,
      },
    ],
  }),
  methods:{
   LastSymbol(s){
     if(s % 10 === 1 && s !== 11) return 'й';
     else if(s % 10 > 1 && s % 10 < 5) return 'я';
    else return 'ев';
  },
  zoomIn(pic){
   this.url = `large_${pic}`;
   this.popup = true;
  }
}
};
</script>
<style>
.v-slide-group {
  display: inline !important;
}
.reviews{
  padding: 35px 30px 32px 31px;
  background-color: white;
  margin-bottom: 50px;
}
.review-item{
  margin-right: 20px;
  padding: 26px 10px 11px 19px;
}
.inner{
  display: flex;
  flex-direction: column;
}
.review-item header{
  display: flex;
  align-items: center;
  margin-bottom: 28px;
}
.review-item .name{margin-left: 10px;}
.city-name{color: #FC4F1E;}
.subtitle{text-transform: uppercase; margin-bottom: 12px;}
.content{
  font-family: Roboto;
font-style: normal;
font-weight: normal;
font-size: 15px;
line-height: 25px;
margin-bottom: 25px;
}
.last::after{
  position:absolute;
  content: "+7";
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  background: rgba(16, 16, 16, 0.4);
  color:white;
  font-size: 17px;
}
.small-text{
  font-family: Roboto;
  color: #9D9D9D;
  font-size: 11px;
}
footer span:nth-child(2){
  margin-left: 10px;
}
footer span:nth-child(2)::before{
    content: "•";
    display: inline-block;
    margin-right: 5px;
}
footer span:last-child{
    padding-left: 20px;
    margin-left: 21px;
    background: url("../assets/thumbUp.svg") no-repeat 0 0;
    background-size: 14px 14px;
    color: #7f7f7f;
    vertical-align: baseline;
}
.all-reviews{
width: 124px;
height: 40px;
border: 2px solid #f72922;
border-radius: 2px;
color: #212121;
font-family: KievitProExtraBold,Roboto,sans-serif;
font-size: 15px;
margin-top: 32px;
}
</style>