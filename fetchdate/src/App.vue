<script setup>
import { ref,onMounted } from 'vue'

const API_URL = `http://localhost:8080/api/students`
const student = ref([])
async function getStudent() {
    try {
        const res = await fetch(`${API_URL}`)
        if (res.ok) return res.json()
        else throw new Error('Error, data is error!')
    } catch (error) {}
}
onMounted(async () => {
  student.value = await getStudent()
  console.log(student.value)
})

</script>

<template>
  <h1>Fetch date from API</h1>
  <p>{{ student[0] }}</p>
  <p>{{ student[1] }}</p>
  <p>{{ student[2] }}</p>
  
</template>
