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
    <button @click="startGame" type="button" :disabled="isPlaying">Play</button>

    <Block @end-game="endGame" v-if="isPlaying" :delay="delay" />
    <Result v-show="showResults" :results="score"/>
  </main>
</template>

<style scoped>

</style>
