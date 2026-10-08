<script setup>
import { ref } from 'vue';

// Guarda o conteúdo preenchido nos campos
const cidade = ref('');
const precoMaximo = ref('');

// Evento enviado ao componente pai
const emit = defineEmits(['buscar']);

function realizarBusca() {
  emit('buscar', {
    cidade: cidade.value,
    precoMaximo: Number(precoMaximo.value),
  });
}

function limparBusca() {
  cidade.value = '';
  precoMaximo.value = '';

  emit('buscar', {
    cidade: '',
    precoMaximo: 0,
  });
}
</script>

<template>
  <section class="filtro">
    <h2>Buscar hotéis</h2>

    <div class="campos">
      <div class="campo">
        <label for="cidade">Cidade</label>

        <input
          id="cidade"
          v-model="cidade"
          type="text"
          placeholder="Ex.: Belém"
        />
      </div>

      <div class="campo">
        <label for="preco">Preço máximo</label>

        <input
          id="preco"
          v-model="precoMaximo"
          type="number"
          min="0"
          placeholder="Ex.: 250"
        />
      </div>

      <button @click="realizarBusca">Buscar</button>

      <button class="botao-limpar" @click="limparBusca">Limpar</button>
    </div>
  </section>
</template>

<style scoped>
.filtro {
  background-color: #edf7ef;
  border: 1px solid #c8e6c9;
  padding: 20px;
  margin-bottom: 24px;
  border-radius: 8px;
}

.filtro h2 {
  margin-top: 0;
}

.campos {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: end;
}

.campo {
  display: flex;
  flex-direction: column;
  flex: 1;
  min-width: 180px;
}

label {
  margin-bottom: 6px;
  font-weight: bold;
}

input {
  padding: 10px;
  border: 1px solid #cccccc;
  border-radius: 5px;
}

button {
  padding: 11px 18px;
  border: none;
  border-radius: 5px;
  background-color: #2e7d32;
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: #256b2a;
}

.botao-limpar {
  background-color: #52796f;
}
</style>
