<template>
    <div class="c-window">
        <header>
          <v-avatar size="44">
            <img
              alt="user"
              :src="require(`../assets/avatars/${user.avatar}`)">
          </v-avatar>
          <div class="user">
            <span class="name">{{user.name}}</span>
            <span class="occupation">{{user.occupation}}</span>
          </div>
          <v-rating v-if="user.rating" class="ml-auto" 
            v-model="user.rating"
            color="yellow darken-3"
            background-color="grey darken-1"
            empty-icon="$ratingFull"
            hover 
            dense
            size="15"
        ></v-rating>
        </header>
        <main>
          <div class="message" :class="{background : h.user === 'user'}"
          v-for="(h, i) in history" 
          :key="i">
            <v-avatar size="44">
              <img
                alt="user"
                :src="require(`../assets/avatars/${avatar(h.user)}`)">
          </v-avatar>
          <div class="content">
            <p>{{h.message}} </p>
            <span class="small-text">{{h.date}}</span>
          </div>
          </div>
        </main>
        <footer>
          <v-avatar size="44">
            <img
              alt="user"
              :src="require(`../assets/avatars/${user.avatar}`)">
          </v-avatar>
          <input type="text" placeholder="Напишите сообщение..." required>
          <button @click="send">
            <img src="../assets/send.png">
          </button>
        </footer>
    </div>
</template>
<script>
export default {
    name: 'ChatWindow',
    props: ["user", "history"],
     data: () => ({
     }),
    methods:{
      avatar(user){
         if(user === "admin")return "avatar1.png";
         else return "avatar2.png";
       },
      send(){
        let inputs = document.querySelectorAll("input");
        for(let i = 0; i < inputs.length; i++){
          console.log(inputs[i].value);
          if(inputs[i].value){
            let obj = {
              user: this.user.status,
              message: inputs[i].value,
              date: "Вчера в 18:45",
            }
            this.$emit('sent', obj);
          inputs[i].value = "";
          }
        }
        
      }
    }
}
</script>
<style>
.c-window{
    width: 415px;
    background-color: white;
    margin-top: 25px;
}
.c-window header{
  padding: 27px 15px 27px 26px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid #EBE9E4;
}
.c-window main{
  height: 500px;
  padding: 14px;
  overflow-y: scroll;
  border-bottom: 1px solid #EBE9E4;
}
.c-window .user{
  display: flex;
  flex-direction: column;
  margin-left: 19px;
}
.c-window footer{
  padding: 25px 55px 30px 25px;
  display: flex;
}
.user .name{
  font-size: 18px;
  line-height: 17px;
  font-weight: bold;
}
.user .occupation{
    display: inline-block;
    padding-left: 10px;
    margin-top: 5px;
    background: url("../assets/flag.svg") no-repeat;
    background-size: 10px 10px;
    color: #FF4641;
    font-size: 13px;
    line-height: 17px;
    vertical-align: baseline;
}
main .message{
  padding: 12px 20px 0 12px;
  display: flex;
}
main .content{margin-left: 20px; margin-bottom: 5px;}
main .message p{
  font-family: KievitProExtraBold,Roboto,sans-serif;
    font-size: 15px;
    line-height: 24px;
    margin-bottom: 0;
}
.background{
  background-color: #F9F7F2;
}
footer input{
  position: relative;
  width: 270px;
height: 49px;
background: #FFFFFF;
border: 1px solid #ECECEC;
padding: 15px 30px 15px 25px;
margin-left: 20px;
}
footer button{
  margin-left: 15px;
}
</style>