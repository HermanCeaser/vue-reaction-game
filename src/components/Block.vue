<script setup>
    import {ref, onMounted} from 'vue'
    
    const showBlock = ref(false)
    const props = defineProps(["delay"])
    const reactionTime = ref(0)
    const emit = defineEmits(['endGame'])
    let timer = null

    onMounted(() => {
        setTimeout(()=>{
            showBlock.value = true
            startTimer()
        }, props.delay)
    })

    function startTimer(){
        timer = setInterval(()=>{
            reactionTime.value += 10
        }, 10)
    }

    function stopTimer(){
        clearInterval(timer)
        emit('endGame', reactionTime.value)
    }

</script>

<template>
  <div @click="stopTimer" v-if="showBlock" class="block">Click me!</div>
</template>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0fa453;
  color: #fff;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
