<script setup>
import { ref } from 'vue'
const playersData = ref([
  {
    id: 1,
    alias: 'Alfred',
    gender: 'male',
    age: 32,
    level: 'Expert',
    numberOfWin: 2,
    actualScore: 0
  },
  {
    id: 2,
    alias: 'Lisa',
    gender: 'female',
    age: 29,
    level: 'Intermediate',
    numberOfWin: 1,
    actualScore: 0
  }
])

const addOnePoint = (index) => {
  playersData.value[index].actualScore += 1
}
const addTwoPoints = (index) => {
  playersData.value[index].actualScore += 2
}
const addThreePoints = (index) => {
  playersData.value[index].actualScore += 3
}
const reset = () => {
  for (let i = 0; i < playersData.value.length; i++) {
    playersData.value[i].actualScore = 0
  }
}
</script>

<template>
  <h1>ScoreBoard</h1>
  <div>
    <div v-for="(player, index) in playersData">
      <h2>{{ player.alias }}</h2>
      <p>{{ player.age }} ans</p>
      <p>level {{ player.level }}</p>
      <p>
        {{ player.gender === 'female' ? 'She' : 'He' }} has already {{ player.numberOfWin }}
        {{ player.numberOfWin > 1 ? 'victories' : 'victory' }}
      </p>
      <p>Actual score</p>
      <p>{{ player.actualScore }}</p>
      <button @click="addOnePoint(index)">Add 1 point</button>
      <button @click="addTwoPoints(index)">Add 2 points</button>
      <button @click="addThreePoints(index)">Add 3 points</button>
    </div>
    <button @click="reset">Reset</button>
  </div>
</template>

<style scoped></style>
