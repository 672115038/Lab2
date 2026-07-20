<script setup lang="ts">
import type { Student } from '@/types'

defineProps<{
  student: Student
}>()
</script>

<template>
  <div class="student-class">
    <div class="student-card">
      <h2>{{ student.name }} {{ student.surname }}</h2>
      <p class="gpa">GPA: {{ student.gpa.toFixed(2) }}</p>
    </div>
  </div>
</template>

<style scoped>
.student-class {
  display: flex;
  justify-content: center;
}

.student-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.student-card:hover {
  transform: scale(1.05);
  box-shadow: 0px 3px 12px 0 rgba(0, 0, 0, 0.2);
}

h2 {
  margin: 0 0 10px 0;
  font-size: 18px;
  color: #2c3e50;
}

.gpa {
  margin: 0;
  font-size: 16px;
  font-weight: bold;
  color: #42b983;
}
</style>
