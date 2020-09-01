<template>
    <div>
        <h1>{{event.title}}</h1>
    </div>
</template>
<script>
export default {
  head() {
    return {
      title: this.event.title ,

      meta: [
        {
          hid:'description',
          name: 'description',
          content: 'what do you want to know about event' + this.event.title,
        }
      ],
    }
  },

  async asyncData({ $axios, error, params }) {
    try{
      const event =  await $axios.$get('events/' + params.id)
      return {
        event
      }
    } catch(e) {
      error ({
        statusCode: 503,
        message:'Unable to show',
      })
    }
  },

  computed: {
      id(){
         return this.$route.params.id
      },
  },
}
</script>