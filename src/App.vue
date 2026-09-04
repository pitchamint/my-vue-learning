<script setup lang="ts">
import { ref } from 'vue'

const firstName = ref('John')
const lastName = ref('Doe')
const age = ref(20)
const gender = ref('<i>Male</i>')

const getFullName = () => {
  return `${firstName.value} ${lastName.value}`
}

</script>
 
<template>
  <section> 
    <p>ชื่อ - สกุล : {{ getFullName() }} อายุ :{{ age }} ปี</p> 
    <p>เพศ <span v-html="gender"></span></p>
    
  </section>
</template>

<style scoped>

</style>
