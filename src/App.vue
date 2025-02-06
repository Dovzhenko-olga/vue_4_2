<template>
<message-item v-for="message in messagesList" :key="message.id"
:userMessage="message" @like="onLike" @dislike="onDislike"/>
<label>
  <input type="text" placeholder="Type a new message" v-model="userMessage">
</label>
<button @click="addMessage">Send</button>
</template>

<script>
import MessageItem from "./components/MessageItem.vue";

export default {
  name: 'App',
  components: {
    MessageItem,
  },
  data() {
    return {
      userMessage: null,
      messagesList: [],
    }
  },
  methods:{
    addMessage(){
      if(this.userMessage)
      this.messagesList.push(
        {id: new Date().getTime(),
          text: this.userMessage,
          likesCount: 0,
        }
      )
        this.userMessage = null
    },
    onLike(idToLike){
      const currentMessage = this.messagesList.find(message=> message.id === idToLike)
      currentMessage.likesCount++
    },
    onDislike(idToDislike){
      const currentMessage = this.messagesList.find(message=> message.id === idToDislike)
      currentMessage.likesCount--
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
