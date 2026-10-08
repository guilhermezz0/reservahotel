<script setup>
defineProps({
  hotel: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(['confirmar']);
</script>

<template>
  <section class="reserva">
    <h2>Resumo da reserva</h2>

    <div class="informacoes">
      <p>
        <strong>Hotel:</strong>
        {{ hotel.nome }}
      </p>

      <p>
        <strong>Cidade:</strong>
        {{ hotel.cidade }}
      </p>

      <p>
        <strong>Valor da diária:</strong>
        R$ {{ hotel.preco }}
      </p>
    </div>

    <button @click="emit('confirmar')">Confirmar reserva</button>
  </section>
</template>

<style scoped>
.reserva {
  margin-top: 30px;
  padding: 24px;
  background-color: #dff3e4;
  border-left: 5px solid #2e7d32;
  border-radius: 5px;
}

.reserva h2 {
  margin-top: 0;
  color: #1b5e3b;
}

.informacoes {
  margin-bottom: 20px;
}

button {
  padding: 12px 20px;
  border: none;
  border-radius: 5px;
  background-color: #198754;
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: #146c43;
}
</style>
