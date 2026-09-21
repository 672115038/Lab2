<script setup lang="ts">
import { useEventStore } from '@/stores/event'
import { storeToRefs } from 'pinia'
import EventService from '@/services/EventService'
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'

const store = useEventStore()
const { event } = storeToRefs(store)
const router = useRouter()
const props = defineProps<{ id: string }>()

onMounted(() => {
  EventService.getEvent(Number(props.id))
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      if (error.response && error.response.status === 404) {
        router.push({ name: '404' })
      } else {
        router.push({ name: 'network-error-view' })
      }
    })
})
</script>
<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <nav>
      <RouterLink :to="{ name: 'event-detail-view' }">Details</RouterLink>
      |
      <RouterLink :to="{ name: 'event-register-view' }">Register</RouterLink>
      |
      <RouterLink :to="{ name: 'event-edit-view' }">Edit</RouterLink>
    </nav>
    <RouterView :event="event" />
  </div>
</template>
