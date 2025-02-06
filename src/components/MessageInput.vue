<template>
  <div>
<label>
  <input type="text" placeholder="Type a new message" v-model="userMessage">
</label>
<button @click="addMessage">Send</button>
  </div>
</template>

<script>
  export default {
    name: 'MessageImput',
    data() {
      return {
        userMessage: null,
      }
    },
    methods: {
      addMessage(){
        if(this.userMessage)
        this.$emit('add', {id: new Date().getTime(),
                          text: this.userMessage,
                          likesCount: 0,})
        this.userMessage = null
    },
    },
  }
</script>

<style lang="scss" scoped>

</style>