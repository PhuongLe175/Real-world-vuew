<template>
  <h1>Event For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event"></EventCard>
  </div>
</template>

<script>
import EventCard from "@/components/EventCard";
import EventService from "@/services/EventService";

export default {
  // eslint-disable-next-line
  name: 'EventList',
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
                .then(response => {
                  this.events = response.data
                })
    .catch(error => {
      console.log(error);
    })
  }
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>