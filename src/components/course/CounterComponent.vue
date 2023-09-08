<script setup>
import { ref, reactive } from 'vue';

const counter = ref(0);

const count = reactive({
  countValue: 1
});

function increment() {
  counter.value = ++counter.value;
  ++count.countValue;
}

function decrement() {
  counter.value = --counter.value;
  --count.countValue;
}

</script>

<template>
  <h2>Counters</h2>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <p>counter is: {{ counter }} </p>
  <p>count is: {{ count.countValue }} </p>
</template>

<style scoped></style>
