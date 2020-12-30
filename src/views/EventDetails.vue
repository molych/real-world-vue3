<template>
  <div v-if="event">
    <hr />
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";
export default {
  props: ["id"],
  data() {
    return {
      event: null
    };
  },
  created() {
    EventService.getEvent(this.id)
      .then(responce => {
        this.event = responce.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>
