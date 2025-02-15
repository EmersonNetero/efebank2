<template>
    <v-container>
      <v-btn color="primary" @click="alerta">Clique aqui</v-btn>
    </v-container>
  </template>
  
  <script setup lang="ts">
  const alerta = () => {
    alert("Botão do Vuetify funcionando!");
  };
  </script>
  