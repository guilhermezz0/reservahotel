# Reserva Fácil

Aplicação web desenvolvida com Vue 3 + Vite para consulta e reserva de hotéis por cidade e faixa de preço.

## Sobre o projeto

O projeto simula uma página de busca de hospedagem, permitindo ao usuário:

- pesquisar hotéis por cidade;
- filtrar por preço máximo;
- visualizar os resultados em cartões;
- selecionar um hotel;
- confirmar a reserva.

A interface foi construída em componentes Vue, com dados estáticos de exemplo para demonstrar o fluxo completo de busca e seleção.

## Funcionalidades

- Busca por cidade;
- Filtro por valor máximo da diária;
- Lista dinâmica de hotéis disponíveis;
- Exibição de mensagem quando nenhum hotel corresponde à busca;
- Seleção de um hotel para reserva;
- Confirmação da reserva com feedback visual.

## Tecnologias utilizadas

- Vue 3
- Vite
- JavaScript
- HTML
- CSS

## Estrutura do projeto

```bash
src/
├── App.vue
├── main.js
├── style.css
├── assets/
├── components/
│   ├── Cabecalho.vue
│   ├── CatalogoHoteis.vue
│   ├── HotelCard.vue
│   ├── HotelFiltro.vue
│   └── Rodape.vue
``` 

## Pré-requisitos

Antes de iniciar, verifique se você possui instalado:

- Node.js 18 ou superior
- npm

## Instalação

1. Clone o repositório:

```bash
git clone <url-do-repositorio>
cd 
```

2. Instale as dependências:

```bash
npm install
```

## Como executar

Inicie o servidor de desenvolvimento:

```bash
npm run dev
```

A aplicação estará disponível em:

```bash
http://localhost:5173
```

## Build de produção

Para gerar a versão otimizada para produção:

```bash
npm run build
```

Para visualizar a build localmente:

```bash
npm run preview
```

## Observações

Este projeto utiliza dados locais em memória e serve como exemplo de uma interface de busca e reserva de hotéis em Vue. Em uma implementação real, seria possível conectar a uma API para carregar hotéis e registrar reservas em back-end.

## Licença

Este projeto está disponível para fins de estudo e demonstração.
