<script setup>
import { ref } from 'vue';

import AppHeader from './components/Cabecalho.vue';
import SearchFilter from './components/HotelFiltro.vue';
import HotelCard from './components/HotelCard.vue';
import BookingSummary from './components/CatalogoHoteis.vue';
import AppFooter from './components/Rodape.vue';

const hoteis = ref([
  {
    id: 1,
    nome: 'Hotel Central',
    cidade: 'Belém',
    preco: 180,
  },
  {
    id: 2,
    nome: 'Hotel Paraíso',
    cidade: 'Salinópolis',
    preco: 250,
  },
  {
    id: 3,
    nome: 'Hotel Praia',
    cidade: 'Belém',
    preco: 220,
  },
  {
    id: 4,
    nome: 'Hotel Amazônia',
    cidade: 'Santarém',
    preco: 200,
  },
]);

const hoteisFiltrados = ref([...hoteis.value]);
const hotelSelecionado = ref(null);
const mensagem = ref('');

function buscar(filtros) {
  mensagem.value = '';
  hotelSelecionado.value = null;

  hoteisFiltrados.value = hoteis.value.filter((hotel) => {
    const cidadeDigitada = filtros.cidade.toLowerCase().trim();

    const mesmaCidade =
      cidadeDigitada === '' ||
      hotel.cidade.toLowerCase().includes(cidadeDigitada);

    const dentroDoPreco =
      !filtros.precoMaximo || hotel.preco <= filtros.precoMaximo;

    return mesmaCidade && dentroDoPreco;
  });
}

function selecionarHotel(hotel) {
  hotelSelecionado.value = hotel;
  mensagem.value = '';
}

function confirmarReserva() {
  mensagem.value = `Reserva no ${hotelSelecionado.value.nome} realizada com sucesso!`;
}
</script>

<template>
  <div class="pagina">
    <AppHeader titulo="Reserva Fácil" />

    <main class="conteudo">
      <section class="apresentacao">
        <h2>Encontre sua próxima hospedagem</h2>

        <p>
          Pesquise hotéis por cidade e escolha uma opção que esteja dentro do
          seu orçamento.
        </p>
      </section>

      <SearchFilter @buscar="buscar" />

      <section class="secao-hoteis">
        <h2>Hotéis disponíveis</h2>

        <div v-if="hoteisFiltrados.length > 0" class="lista-hoteis">
          <HotelCard
            v-for="hotel in hoteisFiltrados"
            :key="hotel.id"
            :hotel="hotel"
            @selecionar="selecionarHotel"
          />
        </div>

        <div v-if="hoteisFiltrados.length === 0" class="sem-resultados">
          <p>😕 Nenhum hotel encontrado.</p>

          <span>
            Tente pesquisar outra cidade ou aumentar o preço máximo.
          </span>
        </div>
      </section>

      <BookingSummary
        v-if="hotelSelecionado"
        :hotel="hotelSelecionado"
        @confirmar="confirmarReserva"
      />

      <div v-show="mensagem" class="mensagem-sucesso">✅ {{ mensagem }}</div>
    </main>

    <AppFooter />
  </div>
</template>

<style scoped>
* {
  box-sizing: border-box;
}

.pagina {
  min-height: 100vh;
  background-color: #f7f8fa;
  color: #12372a;
  font-family: Arial, Helvetica, sans-serif;
}

.conteudo {
  width: 90%;
  max-width: 1100px;
  margin: 0 auto;
  padding: 30px 0;
}

.apresentacao {
  margin-bottom: 30px;
  text-align: center;
}

.apresentacao h2 {
  margin-bottom: 10px;
  color: #1b5e3b;
  font-size: 28px;
}

.apresentacao p {
  max-width: 600px;
  margin: 0 auto;
  color: #45634e;
  line-height: 1.5;
}

.secao-hoteis {
  margin-top: 30px;
}

.secao-hoteis h2 {
  margin-bottom: 20px;
}

.lista-hoteis {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.sem-resultados {
  padding: 30px;
  background-color: white;
  border: 1px solid #dddddd;
  border-radius: 8px;
  text-align: center;
}

.sem-resultados p {
  margin: 0 0 8px;
  font-size: 20px;
  font-weight: bold;
}

.sem-resultados span {
  color: #666666;
}

.mensagem-sucesso {
  margin-top: 20px;
  padding: 16px;
  background-color: #dff5e5;
  border: 1px solid #198754;
  border-radius: 6px;
  color: #146c43;
  font-weight: bold;
  text-align: center;
}

@media (max-width: 600px) {
  .conteudo {
    width: 94%;
  }

  .apresentacao h2 {
    font-size: 23px;
  }

  .lista-hoteis {
    flex-direction: column;
  }
}
</style>
