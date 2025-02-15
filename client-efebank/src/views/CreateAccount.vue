<script setup lang="ts">
import { ref } from 'vue';
import axios from "axios";


const conta = ref({
  nome: "",
  cpf: "",
  saldo: 0,
  tipo: "corrente",
});

const criarConta = async () => {
  try {
    const response = await axios.post("http://localhost:3000/contas", conta.value);
    alert("Conta criada com sucesso!");
    console.log(response.data);
  } catch (error) {
    console.error("Erro ao criar conta", error);
    alert("Erro ao criar conta");
  }
};
</script>
<template>
    <div class="container mt-5">
      <h2>Criação de Conta Bancária</h2>
      <form @submit.prevent="criarConta">
        <div class="mb-3">
          <label for="nome" class="form-label">Nome</label>
          <input type="text" id="nome" v-model="conta.nome" class="form-control" required />
        </div>
        
        <div class="mb-3">
          <label for="cpf" class="form-label">CPF</label>
          <input type="text" id="cpf" v-model="conta.cpf" class="form-control" required />
        </div>
        
        <div class="mb-3">
          <label for="saldo" class="form-label">Saldo Inicial</label>
          <input type="number" id="saldo" v-model="conta.saldo" class="form-control" required />
        </div>
        
        <div class="mb-3">
          <label class="form-label">Tipo de Conta</label>
          <select v-model="conta.tipo" class="form-select">
            <option value="corrente">Conta Corrente</option>
            <option value="poupanca">Conta Poupança</option>
          </select>
        </div>
        
        <button type="submit" class="btn btn-primary">Criar Conta</button>
      </form>
    </div>
  </template>
  

  
  <style scoped>
  .container {
    max-width: 500px;
    background: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  </style>
  