<template>
  <div>
    <h1>Events</h1>
    <EventCard v-for="(event, index) in events" :key="index" :event="event" :data-index="index" />
  </div>
</template>
<script>
import EventCard from '@/components/EventCard.vue'
export default {
  components: {
    EventCard,
  },
  head() {
    return {
      title: 'Event Listening',
    }
  },

  async asyncData({ $axios, error }) {
    try{
      const events =  await $axios.$get('http://localhost:3000/api/events')
      return {
        events
      }
    } catch(e) {
      error ({
        statusCode: 503,
        message:'Unable to show',
      })
    }
  },
}
</script>