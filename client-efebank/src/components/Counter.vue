<template>
    <div>
      <h2>Contador: {{ counter.count }}</h2>
      <button @click="counter.increment">Incrementar</button>
    </div>
  </template>
  
  <script setup lang="ts">
  import { useCounterStore } from "../store/counter";
  const counter = useCounterStore();
  </script>
  