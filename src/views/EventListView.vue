<script setup>
import EventCard from '../components/EventCard.vue';
import { onMounted, ref } from 'vue';
import EventSerivce from '../services/EventService.js';

const events = ref(null)

onMounted(() => {
  EventSerivce.getEvents()
  .then((response) => {
    events.value = response.data
  
  }).catch((error) => {
    console.log(error)
  })
})
</script>

<template>
  <h1>Events for good</h1>
  <div class="events">
  <EventCard v-for="event in events" :key="event.id" :event="event"/>
</div>
</template>

<style scroped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>