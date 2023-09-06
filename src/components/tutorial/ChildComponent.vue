<script setup>
import { ref } from 'vue';

import PropsChildComp from './PropsChildComp.vue';
import EmitsChildComp from './EmitsChildComp.vue';
import SlotsChildComp from './SlotsChildComp.vue';

const greeting = ref('Hello from parent');
const childMsg = ref('No child msg yet');
const msg = ref('from parent')

</script>

<template>
  <h1>Child components</h1>

  <PropsChildComp :msg="greeting" />
  <br>

  <EmitsChildComp @response="(msg) => childMsg = msg" />
  <p>Child message: {{ childMsg }}</p>
  <br>

  <!-- <SlotsChildComp /> -->
  <SlotsChildComp> Message: {{ msg }}</SlotsChildComp>
</template>
