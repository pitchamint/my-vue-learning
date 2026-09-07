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
const isVisible = ref(false)

let nickname = ref('')
const setNickName = (event: Event) => {
  nickname.value = (event.target as HTMLInputElement).value
}

const submitFrom = () => {
  alert(`บันทึกชื่อเล่น : ${nickname.value} สำเร็จ`)
}

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

const toggleVisible = () => {
  isVisible.value = !isVisible.value
}
</script>

<template>
  <section>
    <img :src="picture" :width="width" :height="height" /> <br />

    <form @submit.prevent="submitFrom()">
      <label for="nickname">ป้อนชื่อเล่น : </label>
      <input type="text" id="nickname" v-model="nickname" v-on:input="setNickName" />
      <button type="submit">บันทึก</button>
    </form>

    <p>ชื่อ - สกุล : {{ getFullName() }}</p>
    <p>ชื่อเล่น : {{ nickname }}</p>
    <p>อายุ :{{ age }} ปี</p>
    <button @click="toggleVisible">{{ isVisible ? 'ซ่อนข้อมูล' : 'แสดงข้อมูล' }}</button>
    <article v-show="isVisible">
      <p>เพศ <span v-html="gender"></span></p>
      <p v-if="hobbies.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก : </p>
        <ul>
          <li v-for="h in hobbies" :key="h">{{ h }}</li>
        </ul>
      </div>
      <p>ทักษะ : </p>
      <ul>
        <li> ภาษาโปรแกรม : {{ skill.name }}</li>
        <li> ระดับ : {{ skill.level }}</li>
      </ul>
    </article>


    <button @click="showInfo">คลิกเพื่อดูข้อมูล</button>
    <button @click="incrementAge(10)">เพิ่มอายุ</button>
    <button @click="decrementAge(5)">ลดอายุ</button>
  </section>
</template>

<style scoped></style>
