<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard
      class="event-card"
      v-for="event in events"
      :key="event.id"
      :event="event"
    />
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import axios from "axios";

export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    };
  },
  created() {
    axios
      .get("http://localhost:3000/events")
      .then(response => {
        this.events = response.data;
        console.log(response.data);
      })
      .catch(error => {
        console.log("There was an error: " + error.response);
      });
  }
};
</script>
