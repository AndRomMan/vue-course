<script setup>

const emit = defineEmits(['response']);
emit('response', 'hello from child');

</script>

<template>
  <h2>Emits child component</h2>
  <p>Some child component can also emit events to the parent</p>
</template>
