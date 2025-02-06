<template>
<message-item v-for="message in messagesList" :key="message.id"
:user-message="message" @like="onLike" @dislike="onDislike"/>
<message-input @add="addMessage"/>
</template>

<script>
import MessageItem from "./components/MessageItem.vue";
import MessageInput from './components/MessageInput.vue';

export default {
  name: 'App',
  components: {
    MessageItem,
    MessageInput,
  },
  data() {
    return {
      messagesList: [],
    }
  },
  methods:{
    addMessage(message){
      this.messagesList.push(message)
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
