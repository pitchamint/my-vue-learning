<script setup lang="ts">
import { ref, computed, watch } from 'vue'

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
const salary = ref(20000)

let nickname = ref('')
const setNickName = (event: Event) => {
  nickname.value = (event.target as HTMLInputElement).value
}

const submitFrom = () => {
  alert(`บันทึกชื่อเล่น : ${nickname.value} สำเร็จ`)
}

const getFullName = computed(() => `${firstName.value} ${lastName.value}`)

const showInfo = () => {
  return alert(`ชื่อ - สกุล : ${getFullName.value}`)
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

const getRandomMethod = () => {
  return Math.floor(Math.random() * 100)
}

const getRandomComputed = computed(() => {
  return Math.floor(Math.random() * 100)
})

const getIncome = computed(() => {
  return salary.value * 12
})

const getPosition = computed(() => {
  return salary.value >= 35000 ? 'Project Manager' : 'Programmer'
})

const addSalary = (amount: number) => {
  salary.value += amount
}

watch(salary, (newSalary) => {
  if (newSalary > 50000) {
    alert('เงินเดือนไม่ควรเกิน 50000')
    setTimeout(() => {
      salary.value = 50000
    }, 1000)
  }
})

</script>

<template>
  <section>
    <img :src="picture" :width="width" :height="height" /> <br />

    <form @submit.prevent="submitFrom()">
      <label for="nickname">ป้อนชื่อเล่น : </label>
      <input type="text" id="nickname" v-model="nickname" v-on:input="setNickName" />
      <button type="submit">บันทึก</button>
    </form>

    <p>ชื่อ - สกุล : {{ getFullName }}</p>
    <p>ชื่อเล่น : {{ nickname }}</p>
    <p>อายุ :{{ age }} ปี</p>

    <p>รายได้ต่อเดือน : {{ salary }} บาท</p>
    <p>รายได้ต่อปี : {{ getIncome }} บาท</p>
    <p>ตำแหน่งงาน : {{ getPosition }}</p>
    <button @click="addSalary(5000)">เพิ่มรายได้</button>
    <button @click="addSalary(-5000)">ลดรายได้</button>

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

    <p>ค่าสุ่มจาก method ครั้งแรก : {{ getRandomMethod() }}</p>
    <p>ค่าสุ่มจาก method ครั้งที่สอง : {{ getRandomMethod() }}</p>

    <p>ค่าสุ่มจาก computed ครั้งแรก : {{ getRandomComputed }}</p>
    <p>ค่าสุ่มจาก computed ครั้งที่สอง : {{ getRandomComputed }}</p>
  </section>
</template>

<style scoped></style>
