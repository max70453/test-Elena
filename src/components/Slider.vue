<template>
 <v-carousel hide-delimiters hide-delimiter-background height="460">
    <v-carousel-item v-for="(item, i) in items"
      :key="i">
      <div class="slider">
        <div class="picture">
          <img :src="require(`../assets/${item.img}`)" alt="barselona">
        </div>
        <div class="description">
            <h2 class="title">{{item.title}}</h2>
            <p>{{item.description}}</p>
            <a :href="`${item.path}`">Читать дальше</a>
          </div>
      </div>
    </v-carousel-item>
 </v-carousel>
</template>
<script>
export default {
    name: "Slider",
    data: () => ({
     model: 0,
      items: [
        {
          img: 'barselona.jpg',
          title: "Барселона — обзор города",
          description: "Барселона с её золотистыми пляжами, архитектурными шедеврами Гауди, многочисленными фестивалями и гастрономическим разнообразием понравилась мне в первый же день пребывания и стала местом, в котором...",
          path: '#',
        },
        {
          img: 'barselona.jpg',
          title: "Барселона — обзор города",
          description: "Барселона с её золотистыми пляжами, архитектурными шедеврами Гауди, многочисленными фестивалями и гастрономическим разнообразием понравилась мне в первый же день пребывания и стала местом, в котором...",
          path: '#',
        },
        {
          img: 'barselona.jpg',
          title: "Барселона — обзор города",
          description: "Барселона с её золотистыми пляжами, архитектурными шедеврами Гауди, многочисленными фестивалями и гастрономическим разнообразием понравилась мне в первый же день пребывания и стала местом, в котором...",
          path: '#',
        },
      ],
    }),
}
</script>
<style>
.slider{
  width: 100%;
  background-color: white;
  display: flex;
  font-family: KievitProExtraBold,Roboto,sans-serif;
}
.picture{
  width: 440px;
  height: 440px;
  background-color: #F9F7F2;
}
.picture img{
  background-size: cover;
}
.title{
  font-weight: bold;
  font-size: 29px;
line-height: 35px;
margin-bottom:19px;
}
.description{
  display: flex;
  flex-direction: column;
  margin: auto;
  margin-left: 29px;
}
.description p{font-family: KievitProExtraBold,Roboto,sans-serif;
  width: 363px;
  /* font-size: 17px;
  line-height: 25px; */
}
.description a{
  display: inline-block;
  margin-top: 6px;
  width: 115px;
  color: black;
  text-decoration:none;
  border-bottom: 3px solid #FF4641;
}
</style>
