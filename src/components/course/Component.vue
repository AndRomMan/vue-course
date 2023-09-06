<script setup>
import { ref } from 'vue';
import { onMounted } from 'vue';

const pElementRef = ref(null);

onMounted(() => {
  console.log('component is now mounted');
  pElementRef.value.textContent = 'mounted!'
})

</script>

<template>
  <h2>Component</h2>
  <p ref="pElementRef">hello</p>
</template>

<style scoped></style>
