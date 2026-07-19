<script setup lang="ts">
import type { Event } from '@/types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="category-organizer">
    <div class="text-row">
      <span class="label">Category:</span>
      <span class="value">{{ event.category }}</span>
    </div>
    <div class="text-row">
      <span class="label">Organizer:</span>
      <span class="value">{{ event.organizer }}</span>
    </div>
  </div>
</template>

<style scoped>
.category-organizer {
  width: 250px;
  text-align: right;
  font-size: 1rem;
  color: #222;
  border: 1px solid #39495c;
  padding: 16px;
  margin-bottom: 18px;
}

.text-row {
  display: flex;
  justify-content: flex-end;
  gap: 0.5rem;
  align-items: center;
  margin-bottom: 0.4rem;
}

.text-row:last-child {
  margin-bottom: 0;
}

.label,
.value {
  font-size: 1rem;
}

.label {
  font-weight: 600;
}
</style>
