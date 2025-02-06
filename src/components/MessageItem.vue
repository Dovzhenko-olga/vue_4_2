<template>
  <div>
<span>{{userMessage.text}}</span>
<button @click="onLike">Like</button>
<button @click="onDislike">Dislike</button>
<span>Likes: {{userMessage.likesCount}}</span>
  </div>
</template>

<script>
  export default {
    name: "MessageItem",
    props: {
      userMessage: {
        type: Object,
        default: ()=>({}),
      },
    },
    methods:{
      onLike(){
        this.$emit('like', this.userMessage.id)
      },
      onDislike(){
        this.$emit('dislike', this.userMessage.id)
      },
    }
  }
</script>

<style lang="scss" scoped>

</style>