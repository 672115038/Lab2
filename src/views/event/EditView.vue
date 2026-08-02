<script setup lang="ts">
import { toRefs } from 'vue'
import { useRouter } from 'vue-router'
import { useMessageStore } from '@/stores/message'
import { type Event } from '@/types'

const props = defineProps<{
  event: Event
}>()
const { event } = toRefs(props)
const router = useRouter()
const store = useMessageStore()

const saveAndViewDetails = () => {
  store.updateMessage('Event data has been updated.')
  router.push({ name: 'event-detail-view', params: { id: event.value.id } })
}
</script>
<template>
  <div>
    <p>Edit event here</p>
    <button @click="saveAndViewDetails">Save and view details</button>
  </div>
</template>
