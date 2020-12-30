<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  name: "Home",
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    };
  },
  created() {
    EventService.getEvents()
      .then(responce => {
        this.events = responce.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
