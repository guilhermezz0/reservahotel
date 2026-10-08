<script setup>
// Dados recebidos do App.vue
defineProps({
  hotel: {
    type: Object,
    required: true,
  },
});

// Evento enviado ao App.vue
const emit = defineEmits(['selecionar']);
</script>

<template>
  <article class="hotel-card">
    <div class="hotel-icone">🏨</div>

    <h3>{{ hotel.nome }}</h3>

    <p>📍 {{ hotel.cidade }}</p>

    <p class="preco">R$ {{ hotel.preco }} / diária</p>

    <button @click="emit('selecionar', hotel)">Reservar</button>
  </article>
</template>

<style scoped>
.hotel-card {
  width: 250px;
  padding: 20px;
  border: 1px solid #c8e6c9;
  border-radius: 8px;
  background-color: #ffffff;
  box-shadow: 0 2px 6px rgba(18, 55, 42, 0.1);
}

.hotel-icone {
  font-size: 40px;
}

.hotel-card h3 {
  color: #1b5e3b;
  margin-bottom: 8px;
}

.preco {
  font-size: 18px;
  font-weight: bold;
  color: #12372a;
}

button {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #2e7d32;
  color: #ffffff;
  cursor: pointer;
}

button:hover {
  background-color: #16a64f;
}
</style>
