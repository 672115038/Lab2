<script setup lang="ts">
import StudentCard from '@/components/StudentCard.vue'
import type { Student } from '@/types'
import { ref, onMounted } from 'vue'
import StudentService from '@/services/StudentService'

const students = ref<Student[] | null>(null)
const error = ref<string | null>(null)

onMounted(() => {
  StudentService.getStudents()
    .then((response) => {
      students.value = response.data
    })
    .catch((err) => {
      console.error('There was an error!', err)
      error.value = 'Failed to load students'
    })
})
</script>

<template>
  <div>
    <h1>Students</h1>

    <div v-if="error" class="error-message">
      {{ error }}
    </div>

    <div v-else-if="students === null" class="loading">Loading...</div>

    <div v-else class="students">
      <div v-for="student in students" :key="student.id">
        <StudentCard :student="student" />
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  margin-top: 20px;
  margin-bottom: 30px;
  color: #2c3e50;
}

.students {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.loading {
  text-align: center;
  padding: 40px;
  font-size: 18px;
  color: #2c3e50;
}

.error-message {
  text-align: center;
  padding: 20px;
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
  border-radius: 4px;
  margin: 20px;
}
</style>
