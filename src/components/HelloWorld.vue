<script setup>
import { ref } from 'vue';
import { reactive } from 'vue';

defineProps({
  msg: String,
  falseMsg: String
})

const awsome = ref(true);
let awsomeText = awsome.value;
console.log(`awsome = ${awsome.value}`);
const count = ref(0);
const message = ref('Hi there!');
const counter = reactive({ counterPoint: 0 });

console.log(`counter.counterPoint = ${counter.counterPoint}`);
console.log(`message.value = ${message.value}`);
message.value = 'changed';
console.log(`message.value = ${message.value}`);

const titleClass = ref('title');

function increment() {
  // update component state
  count.value++;
  console.log(`count is changed ${count.value}`);
}

function toggle() {
  console.log('--------------------');
  console.log(`awsome before = ${awsome.value}`);
  awsome.value = !awsome.value;
  console.log(`awsome after = ${awsome.value}`);
  awsomeText = awsome.value;
  console.log(`awsomeText = ${awsomeText}`);
  console.log('--------------------');
}

const text = ref('');

function onInput(evt) {
  text.value = evt.target.value;
  console.log(`text is changed ${text.value}`);

}

</script>

<template>
  <h1 v-if="awsome">{{ msg }}</h1>
  <h1 v-else>{{ falseMsg }}</h1>

  <div class="card">
    <h2 :class="titleClass">Make me red</h2>
    <p>{{ message.split('').reverse().join('') }}</p>
    <button @click="toggle">Change the Awsome is: {{ awsomeText }} </button>
    <br>
    <br>
    <button type="button" @click="counter.counterPoint++">count is {{ counter.counterPoint }}</button>
    <br>
    <br>
    <button type="button" @click="increment">count is {{ count }}</button>
    <br>
    <br>
    <input :value="text" @input="onInput" placeholder="Type here">
    <br>
    <input v-model="text" placeholder="Type here">
    <br>
    <p>{{ text }}</p>
  </div>
</template>

<style scoped>
.title {
  color: red;
}
</style>

