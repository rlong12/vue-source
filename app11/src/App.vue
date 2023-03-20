<script setup>
import { ref, provide } from 'vue'
import Middle from './components/Middle.vue'

const msg = ref("")

provide('message', msg)
</script>

<template>
  <div>
    <h1>Parent Component. This takes a message from the user and Provides it. It imports the Middle Component</h1>
    <section>
      <label for="text">Enter a message:</label>
      <input type="text" id="text" name="text" v-model="msg">
    </section>
    <br>
    <Middle id="middle"></Middle>
  </div>
</template>

<style>
section,
h1 {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

div {
  background-color: aquamarine;
  padding: 50px;
}

#middle {
  display: flex;
  justify-content: center;
  margin: 100px;
}

label {
  scale: 1.5;
}

input {
  scale: 1.5;
  position: relative;
  top: 30px;
}
</style>
