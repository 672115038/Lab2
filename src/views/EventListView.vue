<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import CategoryOrganizer from '@/components/CategoryOrganizer.vue'
import type { Event } from '@/types'
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'
// const events = ref<Event[]>([
//   {
//     id: 5928101,
//     category: 'animal welfare',
//     title: 'Cat Adoption Day',
//     description: 'Find your new feline friend at this event.',
//     location: 'Meow Town',
//     date: 'January 28, 2026',
//     time: '12:00',
//     petsAllowed: true,
//     organizer: 'Kat Laydee',
//   },
//   {
//     id: 4582797,
//     category: 'food',
//     title: 'Community Gardening',
//     description: 'Join us as we tend to the community edible plants.',
//     location: 'Flora City',
//     date: 'March 14, 2026',
//     time: '10:00',
//     petsAllowed: true,
//     organizer: 'Fern Pollin',
//   },
//   {
//     id: 8419988,
//     category: 'sustainability',
//     title: 'Beach Cleanup',
//     description: 'Help pick up trash along the shore.',
//     location: 'Playa Del Carmen',
//     date: 'July 22, 2026',
//     time: '11:00',
//     petsAllowed: false,
//     organizer: 'Carey Wales',
//   },
// ])
const events = ref<Event[] | null>(null)

onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>

  <div class="events">
    <div v-for="event in events" :key="event.id" class="event-pair">
      <EventCard :event="event" />
      <CategoryOrganizer :event="event" />
    </div>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.event-pair {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}

@media (min-width: 640px) {
  .event-pair {
    flex-direction: row;
    align-items: flex-start;
  }
}
</style>
