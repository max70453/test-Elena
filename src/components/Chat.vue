<template>
    <div class="chatroom">
        <div class="first">
          <h2>Чат с пользователем</h2>
            <ChatWindow @sent="addMessage" :user = "users[1]" :history =  "history"/>
        </div>
        <div class="second">
          <h2>Чат с администратором</h2>
          <ChatWindow @sent="addMessage" :user = "users[0]" :history =  "history"/>
        </div>
    </div>
</template>
<script>
export default {
    name: "Chat",
    components:{
       ChatWindow: () => import("@/components/ChatWindow.vue"),
    },
    data: () => ({
      users: [
        {
          status: 'admin',
          avatar: "avatar1.png",
          name: "Администратор",
          occupation: "Администратор",
        },
        {
          status: 'user',
          avatar: "avatar2.png",
          name: "Наталия Полянская",
          rating: 4,
          occupation: "Гид по Баварии, фотограф"
        }
      ],
      history: [
         {
           user: 'admin',
           message: "Из достопримечательностей могу предложить обратить внимание на вулкан Майон, путешествие запомнится вам надолго хотя бы из-за невероятной сложности подъема на него. Поверьте, это стоит того; также хотелf бы отметить очень важную область исследования",
           date: "Вчера в 17:45",
         },
         {
           user: 'user',
           message: "Что из себя представляет вулкан? Просто хочу убедиться, что готова к такому путешествию.",
           date: "Вчера в 18:45",
         },
         {
           user: 'admin',
           message: "Из достопримечательностей могу предложить обратить внимание на вулкан Майон, путешествие запомнится вам надолго хотя бы из-за невероятной сложности подъема на него. Поверьте, это стоит того; также хотелf бы отметить очень важную область исследования",
           date: "Вчера в 17:45",
         },
         {
           user: 'user',
           message: "Что из себя представляет вулкан? Просто хочу убедиться, что готова к такому путешествию.",
           date: "Вчера в 18:45",
         },
           {
           user: 'admin',
           message: "Из достопримечательностей могу предложить обратить внимание на вулкан Майон, путешествие запомнится вам надолго хотя бы из-за невероятной сложности подъема на него. Поверьте, это стоит того; также хотелf бы отметить очень важную область исследования",
           date: "Вчера в 17:45",
         },
       ],
    }),
    methods:{
      addMessage(message){
        this.history.push(message);
      }
    }
}
</script>
<style>
.chatroom{
    display: grid;
     grid-template-columns: 430px 430px;
}
.chatroom .first{
  border-right: 1px solid #EBE9E4;
}
.chatroom .second{
  border-left: 1px solid #EBE9E4;
  padding-left: 15px;
}
</style>