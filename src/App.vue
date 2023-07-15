<script setup>
import {ref} from 'vue'
import Block from './components/Block.vue';
import Result from './components/Result.vue';

// Reactive state
const isPlaying = ref(false);
const delay = ref(null);
const showResults = ref(false);
let score = null;

function startGame(){
  delay.value = 2000 + Math.floor(Math.random()* 5000)
  isPlaying.value = true
  showResults.value=false
}

function endGame(reactionTime){
  score = reactionTime
  isPlaying.value = false
  showResults.value = true
}
</script>

<template>
  <main>
    <h1>Reaction Timer Game.</h1>
    <button class="btn" @click="startGame" type="button" :disabled="isPlaying">Play</button>

    <Block @end-game="endGame" v-if="isPlaying" :delay="delay" />
    <Result v-if="showResults" :results="score"/>
  </main>
</template>

<style scoped>
  main {
    display: flex;
    flex-direction: column;
  }
  .btn {
    padding: 10px 0;
    border-radius: 50px;
    border: none;
    background-color: #11ae54;
    color: white;
    /* font-size: 1.2em; */
    margin-bottom: 20px;
    font-weight: 700;
  }

  .btn:hover {
    background-color: #00ff6e;
  }

  .btn:disabled:hover {
    cursor: not-allowed;
    background-color: #11ae54;
  }
</style>
