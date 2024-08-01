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
const pointsValueList = ref([1, 2, 5])

const addOnePoint = (index, numberPoint) => {
  playersData.value[index].actualScore += numberPoint
}

const reset = () => {
  for (let i = 0; i < playersData.value.length; i++) {
    playersData.value[i].actualScore = 0
  }
}
</script>

<template>
  <main>
    <h1>ScoreBoard</h1>
    <div class="player-card">
      <div v-for="(player, index) in playersData">
        <div class="player">
          <h2>{{ player.alias }}</h2>
          <p>{{ player.age }} ans</p>
          <p>level {{ player.level }}</p>
        </div>

        <p class="victory">
          {{ player.gender === 'female' ? 'She' : 'He' }} has already
          <span>{{ player.numberOfWin }}</span>
          {{ player.numberOfWin > 1 ? 'victories' : 'victory' }}
        </p>
        <div class="score">
          <p>Actual score</p>
          <p>{{ player.actualScore }}</p>
        </div>
        <div class="pointBloc">
          <button v-for="point in pointsValueList" @click="addOnePoint(index, point)">
            Add {{ point }} point
          </button>
        </div>
      </div>
    </div>
    <button class="reset" @click="reset">Reset</button>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.player-card {
  display: flex;
  align-items: center;
}
.player-card > div {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 20px;
  margin-bottom: 32px;
}
.player {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 16px;
  line-height: 20px;
}
.victory {
  margin-bottom: 32px;
  font-size: 24px;
  font-weight: bold;
}
span {
  color: var(--orange);
}
.score {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 40px;
}
.score p:first-child {
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 10px;
}
.score p:last-child {
  font-size: 36px;
  width: 60px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--orange);
  border-radius: 50%;
}
.player-card > div:first-child {
  border-right: 1px solid var(--orange);
}
.pointBloc {
  display: flex;
  gap: 20px;
}
button {
  padding: 5px 10px;
  background-color: white;
  border-radius: 8px;
  border: 2px solid var(--orange);
  color: var(--orange);
  font-family: 'Play', sans-serif;
}
button:hover {
  background-color: var(--orange);
  cursor: pointer;
  color: white;
  scale: 1.2;
  transition: scale 0.5s;
}
button:active {
  opacity: 50%;
}
.reset {
  border: 2px solid grey;
  color: grey;
}
.reset:hover {
  border: solid grey;
  color: white;
  background-color: gray;
}
</style>
