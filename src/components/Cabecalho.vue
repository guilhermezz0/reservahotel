<script setup>
// Recebe o título definido pelo App.vue
defineProps({
  titulo: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <header class="cabecalho">
    <div>
      <h1>{{ titulo }}</h1>
      <p>Encontre um hotel para a sua próxima viagem</p>
    </div>
  </header>
</template>

<style scoped>
.cabecalho {
  background-color: #16a64f;
  color: #ffffff;
  padding: 24px;
  text-align: center;
}

.cabecalho h1 {
  margin: 0;
  font-size: 32px;
}

.cabecalho p {
  margin: 8px 0 0;
}
</style>
