<template>
  <div v-if="event">
    <h1>
      <span>Event # {{ $route.params.id }}</span>
      {{ event.title }}
    </h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
<script>
import EventService from '@/services/EventService'

export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventService.getEventById(this.id)
      .then((response) => {
        this.event = response.data
      })
      .catch((err) => {
        console.log('error: ', err)
      })
  },
}
</script>
