<template>
  <div>
    <div class="mb-5">
      <button class="btn btn-success mx-2" @click="change">add</button>
      {{ name }}
      <button class="btn btn-danger mx-2" @click="changeN">next</button>
    </div>
    <table class="table">
      <thead class="table-header">
        <tr>
          <th>T/R</th>
          <th>name</th>
          <th>age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in arr">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
        </tr>
      </tbody>
    </table>

    <div class="text-center">
      <h3>{{ yurish }}</h3>
      <button @click="yurishQadam" class="btn btn-info">qadam tashlash</button>
    </div>
    <div class="text-center">
      <h2>{{ qadam }}</h2>
      <button @click="pulsQadam" class="btn btn-primary">qadamni qo'shish +1</button>
    </div>


    <div class="mt-3 text-center">
      <button @click="addUser" class="btn btn-success"> add count</button>
      <ul class="mt-3">
        <li v-for="(item, index) in countArr" class="d-flex gap-3 my-2">
          <button @click="() => puls(index)" class="btn btn-info">+</button>
          <h4>{{ item.counts }}</h4>
          <button :id="item.id" @click="minus" class="btn btn-danger">-</button>
        </li>
      </ul>
    </div>
  </div>
</template>
 
<script setup>
import { ref } from 'vue';
const name = ref(0);
const qadam = ref(0)
const yurish = ref(0)
const counts = ref(0)
const countArr = ref([])
const addUser = () => {
  countArr.value.push({ id: countArr.value.length - 0, counts: counts })
}

const puls = (index) => {
  // countArr[index].counts.value += 1
  console.log(countArr[index].target
  
  )
}
const minus = (e) => {
  countArr._rawValue.find((item) => {
    if (item.id == e.target.id) {
      counts.value -= 1
    }
  })
}
const arr = ref([
  { id: 1, name: 'Nodir', age: 19 },
  { id: 2, name: 'Nodirbek', age: 29 },
  { id: 3, name: 'Nodirjon', age: 39 },
])
const pulsQadam = () => {
  qadam.value += 1
}
const yurishQadam = () => {
  yurish.value += qadam.value
}
const change = () => {
  name.value += 1
}
const changeN = () => {
  name.value -= 1
}



</script>

<style scoped>
div {
  color: rgb(19, 19, 19);
}
</style> 