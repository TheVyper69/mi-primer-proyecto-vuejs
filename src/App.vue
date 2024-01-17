<script setup>
  import {ref, computed } from 'vue'
  const name="willian"

  let counter = ref(0)

  const arrayfav = ref([])

  const increment = () =>{

    counter.value++

  }

  const restar = () => {
    counter.value--
  }
  const reset = () => {
    counter.value = 0
  }

  const add = () => {
    arrayfav.value.push(counter.value)
  }

  const blockBtn = computed(()=>{
    const numSerch = arrayfav.value.find((num) => num === counter.value)
    if(numSerch === 0) return true
    return numSerch ? true : false
  })

</script>

<template>
  <div class="container text-center mt-3">

    <h1>Hola {{ name }}</h1>

    <h2 v-if=" counter > 0 " style="color: green;">clicks {{ counter }}</h2>
    <h2 v-else-if="counter < 0 " style="color: red;">clicks {{ counter }}</h2>
    <h2 v-else>clicks {{ counter }}</h2>


    <div class="btn-group" role="group" aria-label="Basic example">
      <button @click="increment" class="btn btn-success">Incremetar</button>

      <button @click="restar" class="btn btn-danger">Restar</button>

      <button @click="reset" class="btn btn-secondary">Reset</button>

      <button @click="add" :disabled="blockBtn" class="btn btn-primary">Add</button>
    </div>
    
    <p></p>

    <ul class="list-group">
      <li class="list-group-item" v-for="num in arrayfav">{{ num }}</li>
    </ul>
  </div>
</template>

<style>
  
</style>