

<template>
<h1>Hola mundo</h1>
<p>{{ contador }}</p>
<button @click="incrementar">incrementar</button>
<button @click="decrementar">decrementar</button>

</template>

<script setup lang="ts">
import { ref } from 'vue';
const contador = ref(0);
const incrementar = ()=>{
  contador.value++;
}
const decrementar = ()=>{
  contador.value--;
}
</script>

<style scoped>
p{
  color: blueviolet;
  font-size: 3rem;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>
