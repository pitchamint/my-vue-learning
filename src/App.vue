<script setup lang="ts">
import { ref } from 'vue'

const firstName = ref('Pitchamint')
const lastName = ref('Lovekirby')
const age = ref(20)
const gender = ref('<i>Female</i>')
const picture = ref('https://upload.wikimedia.org/wikipedia/en/4/4e/Kirby_Nintendo.png?utm_source=en.wikipedia.org&utm_campaign=index&utm_content=original')
const size = ref(200)
const hobbies = ref(['Reading', 'Traveling', 'Photography'])
const skill = ref(
  {
    name: 'HTML',
    level: 'Expert'
  })


const getFullName = () => {
  return `${firstName.value} ${lastName.value}`
}
</script>
 
<template>
  <section> 
    <img :src="picture" :width="size" :height="size" />
    <p>ชื่อ - สกุล : {{ getFullName() }}</p> 
    <p>อายุ :{{ age }} ปี</p>
    <p>เพศ <span v-html="gender"></span></p>
    <p>งานอดิเรก : </p>
    <ul>
      <li v-for="h in hobbies" :key="h">{{ h }}</li>
    </ul>
    <p>ทักษะ : </p>
    <ul>
      <li> ภาษาโปรแกรม : {{ skill.name }}</li>
      <li> ระดับ : {{ skill.level }}</li>
    </ul>
  </section>
</template>

<style scoped>

</style>
