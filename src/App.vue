<script setup lang="ts">
import { ref } from 'vue'

const firstName = ref('John')
const lastName = ref('Doe')
const age = ref(20)
const gender = ref('<i>Male</i>')
const picture = ref('https://www.flaticon.com/free-icon/proud_10623149?related_id=10623149')
const size = ref(150)

const getFullName = () => {
  return `${firstName.value} ${lastName.value}`
}

</script>
 
<template>
  <section> 
    <img :src="picture" :width="size" :height="size" />
    <p>ชื่อ - สกุล : {{ getFullName() }} อายุ :{{ age }} ปี</p> 
    <p>เพศ <span v-html="gender"></span></p>
  </section>
</template>

<style scoped>

</style>
