<script setup lang="ts">
import { ref, watch } from "vue";
import axios from "axios";

enum AccountType {
  PAYMENT = "PAYMENT",
  CURRENT = "CURRENT",
}

enum HolderType {
  NATURAL = "NATURAL",
  LEGAL = "LEGAL",
}

enum AccountStatus {
  ACTIVE = "ACTIVE",
  BLOCKED = "BLOCKED",
  FINISHED = "FINISHED",
}

const conta = ref({
  branch: "",
  type: AccountType.CURRENT,
  holderName: "",
  holderEmail: "",
  holderType: HolderType.NATURAL,
  holderDocument: "",
  status: AccountStatus.ACTIVE, 
});


watch(
  () => conta.value.holderType,
  () => {
    conta.value.holderDocument = "";
  }
);


const criarConta = async () => {
  try {
    const response = await axios.post(
      "http://localhost:3000/contas",
      conta.value
    );
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
      <!-- Agência (Branch) -->
      <div class="mb-3">
        <label for="branch" class="form-label">Agência</label>
        <input
          type="text"
          id="branch"
          v-model="conta.branch"
          class="form-control"
          required
        />
      </div>

      <!-- Tipo de Conta (Type) -->
      <div class="mb-3">
        <label for="type" class="form-label">Tipo de Conta</label>
        <select id="type" v-model="conta.type" class="form-select" required>
          <option :value="AccountType.CURRENT">Conta Corrente</option>
          <option :value="AccountType.PAYMENT">Conta Pagamento</option>
        </select>
      </div>

      <!-- Nome do Titular (Holder Name) -->
      <div class="mb-3">
        <label for="holderName" class="form-label">Nome do Titular</label>
        <input
          type="text"
          id="holderName"
          v-model="conta.holderName"
          class="form-control"
          required
        />
      </div>

      <!-- E-mail do Titular (Holder Email) -->
      <div class="mb-3">
        <label for="holderEmail" class="form-label">E-mail do Titular</label>
        <input
          type="email"
          id="holderEmail"
          v-model="conta.holderEmail"
          class="form-control"
          required
        />
      </div>

      <!-- Tipo Legal do Titular (Holder Type) -->
      <div class="mb-3">
        <label for="holderType" class="form-label">Tipo Legal do Titular</label>
        <select
          id="holderType"
          v-model="conta.holderType"
          class="form-select"
          required
        >
          <option :value="HolderType.NATURAL">Pessoa Física</option>
          <option :value="HolderType.LEGAL">Pessoa Jurídica</option>
        </select>
      </div>

      <!-- Documento (Holder Document) -->
      <div class="mb-3">
        <label for="holderDocument" class="form-label">
          {{ conta.holderType === HolderType.NATURAL ? "CPF" : "CNPJ" }}
        </label>
        <input
          type="text"
          id="holderDocument"
          v-model="conta.holderDocument"
          class="form-control"
          :placeholder="
            conta.holderType === HolderType.NATURAL
              ? '000.000.000-00'
              : '00.000.000/0000-00'
          "
          required
        />
      </div>

      <!-- Status da Conta (Account Status) -->
      <div class="mb-3">
        <label for="status" class="form-label">Status da Conta</label>
        <select id="status" v-model="conta.status" class="form-select" required>
          <option :value="AccountStatus.ACTIVE">Ativa</option>
          <option :value="AccountStatus.BLOCKED">Bloqueada</option>
          <option :value="AccountStatus.FINISHED">Finalizada</option>
        </select>
      </div>

      <!-- Botão de Envio -->
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
