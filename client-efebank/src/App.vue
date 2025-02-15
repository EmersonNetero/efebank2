<template>
  <v-app>
    <v-container>
      <nav>
        <router-link to="/">Home</router-link> |
        <router-link to="/about">Sobre</router-link>
      </nav>
      <router-view />
    </v-container>
  </v-app>
</template>
