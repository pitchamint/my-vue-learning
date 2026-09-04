<script setup lang="ts">
import { ref } from 'vue'

const firstName = ref('Pitchamint')
const lastName = ref('Lovekirby')
const age = ref(20)
const gender = ref('<i>Female</i>')
const picture = ref('https://upload.wikimedia.org/wikipedia/en/4/4e/Kirby_Nintendo.png?utm_source=en.wikipedia.org&utm_campaign=index&utm_content=original')
const height = ref(200)
const width = ref(250)
const hobbies = ref(['Reading', 'Traveling', 'Photography'])
const skill = ref(
  {
    name: 'HTML',
    level: 'Expert'
  })


const getFullName = () => {
  return `${firstName.value} ${lastName.value}`
}

const showInfo = () => {
  return alert(`ชื่อ - สกุล : ${getFullName()}`) 
}

const incrementAge = (ageIn: number) => {
  age.value += ageIn
}

const decrementAge = (ageDec: number) => {
  age.value -= ageDec
}
</script>
 
<template>
  <section> 
    <img :src="picture" :width="width" :height="height" />
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

    <button @click="showInfo">คลิกเพื่อดูข้อมูล</button>
    <button @click="incrementAge(10)">เพิ่มอายุ</button>
    <button @click="decrementAge(5)">ลดอายุ</button>
  </section>
</template>

<style scoped>

</style>
