<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>EFE-bank</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn text to="/">Home</v-btn>
      <v-btn text to="/about">Sobre</v-btn>
      <v-btn text to="/createAccount">Criar uma conta</v-btn>
    </v-app-bar>

    <v-main>
      <v-container>
        <router-view />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style scoped>
/* Estilos adicionais podem ser definidos aqui */
</style>

