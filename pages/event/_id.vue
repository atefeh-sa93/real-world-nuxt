<template>
    <div>
        <h1>Event #{{id}}</h1>
    </div>
</template>
<script>
export default {
  head() {
    return {
      title: 'Events #' + this.id ,

      meta: [
        {
          hid:'description',
          name: 'description',
          content: 'what do you want to know about event' + this.id,
        }
      ],
    }
  },

  computed: {
      id(){
         return this.$route.params.id
      },
  },
}
</script>