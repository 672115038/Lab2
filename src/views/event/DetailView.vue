<script setup lang="ts">
import { toRefs, onMounted } from 'vue'
import { useMessageStore } from '@/stores/message'
import { type Event } from '@/types'

const props = defineProps<{
  event: Event
}>()
const { event } = toRefs(props)
const store = useMessageStore()

onMounted(() => {
  if (store.message) {
    setTimeout(() => {
      store.resetMessage()
    }, 3000)
  }
})
</script>
<template>
  <div>
    <div v-if="store.message" id="flashMessage">
      <h4>{{ store.message }}</h4>
    </div>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
