<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>Props child component</h2>
  <h3>{{ msg || 'No props passed yet' }}</h3>
</template>
