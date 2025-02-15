<template>
  <v-app>
    <v-container class="d-flex justify-center align-center" style="min-height: 100vh;">
      <v-card class="pa-5" max-width="400" outlined>
        <v-card-title class="text-h5 text-center">Bem-vindo ao EFEbank</v-card-title>
        <v-card-subtitle class="text-center">
          <p class="subheading">Escolha uma opção para continuar</p>
        </v-card-subtitle>
        <v-card-actions class="d-flex justify-center">
          <v-btn color="primary" class="mx-2" large @click="logar">
            Logar
          </v-btn>
          <v-btn color="secondary" class="mx-2" large @click="criarConta">
            Criar Conta
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
  </v-app>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter(); 


const logar = () => {
 
  console.log('Redirecionando para a tela de login...');
  router.push('/bankAccount');
};

const criarConta = () => {
 
  console.log('Redirecionando para a tela de criação de conta...');
  router.push('/createAccount');
};
</script>

<style scoped>
.v-card {
  background-color: #ffffff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
}
</style>
