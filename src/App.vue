<template>
  <v-app >
    <v-main class="main-div">
      <v-container class="container-main">
        <Slider />
        <About />
        <Chat />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  components: {
    Slider: () => import("@/components/Slider.vue"),
    About: () => import("@/components/About.vue"),
    Chat: () => import("@/components/Chat.vue"),
  },

  data: () => ({
    //
  }),
};
</script>
<style>
.v-application{
    font-family: KievitProExtraBold,Roboto,sans-serif;
    line-height: 25px;
}
.v-application p{
  margin-bottom:0;
}
.main-div{
background-color: #F9F7F2;
margin: 0;
padding: 0;
}
.container{
  padding: 0;
}
.container-main{
max-width: 879px !important;
margin-top: 110px;
margin-bottom: 134px; 
}
.col{padding:0 10px;}
</style>
