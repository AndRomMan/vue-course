<script setup>
import { ref, reactive, computed } from 'vue';

const users = ref([
  {
    id: 1,
    name: 'Alice',
    age: 19
  },
  {
    id: 2,
    name: 'Kate',
    age: 40
  },
  {
    id: 3,
    name: 'Anna',
    age: 50
  },
  {
    id: 3,
    name: 'Tara',
    age: 17
  },
]);
const products = ref([
  'car', 'horse', 'doll', 'puppy', 'apple', 'cube', 'monkey', 'cat', 'dog'
]);

const query = ref('');

const productQuery = computed(() => {
  return products.value.filter((prod) => prod.indexOf(query.value) !== -1);
}
);
</script>

<template>
  <h2>Object list</h2>
  <ul>
    <li v-for="user in users" :key="user.id">
      <p>{{ user.name }} — <spanv :class="{ 'redText': user.age > 30 }">{{ user.age }}</spanv>
      </p>

    </li>
  </ul>

  <h2>Array list</h2>

  <input type="search" placeholder="Поиск товаров" v-model="query">
  <p>Search resault is: {{ query }}</p>

  <ul>
    <li v-for="product in productQuery" :key="product">
      <p>{{ product }}</p>
    </li>
  </ul>
</template>

<style scoped>
.redText {
  color: red;
}
</style>
