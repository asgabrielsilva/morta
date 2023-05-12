<script setup>
 import { ref } from 'vue'

const produtos = ref([
   {
       id: 1,
       nome: 'Camiseta',
       preco: 49.90,
       quantidade: 0,
       valorTotal: 49.90

   },
   {
       id: 2,
       nome: 'Calça',
       preco: 99.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 3,
       nome: 'Meia',
       preco: 9.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 4,
       nome: 'Sapato',
       preco: 199.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 5,
       nome: 'Boné',
       preco: 29.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 6,
       nome: 'Óculos',
       preco: 99.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 7,
       nome: 'Relógio',
       preco: 299.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 8,
       nome: 'Bermuda',
       preco: 79.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 9,
       nome: 'Cueca',
       preco: 19.90,
       quantidade: 0,
       valorTotal: 49.90
   },
   {
       id: 10,
       nome: 'Meia',
       preco: 9.90,
       quantidade: 0,
       valorTotal: 49.90
   }
])
const carrinhoCompras = ref([

])
const listaCompras = ref([
   { nome: 'arroz', quantidade: 1 },
   { nome: 'batata', quantidade: 2 },
   { nome: 'feijão', quantidade: 3 }
 ])
</script>

<template>
  <div class="row">
 <div class="card" style="width: 15rem;" v-for="(item) in produtos" :key="item.id">
  <div class="card-body">
    <h5 class="card-title">{{ item.nome }}</h5>
    <p class="card-text"> texto</p>
  </div>
  <ul class="list-group list-group-flush" >
    <li class="list-group-item">
  <p>Preço: R${{ item.preco }}</p></li>
  </ul>
  <div class="card-body">
    <a href="#" class="card-link">Card link</a>
    <button type="button" class="btn btn-primary">Comprar</button>
  </div>
</div>
</div>
</template>

<style scoped>
  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
  }


.card{
  display: flex;
  margin: 5px;
  justify-content: center;
  align-items: center;
  border-style: solid;
  border-radius: 20px;
      border-color: #868686;
      border-width: 3px;
  
}

.row {
  display: flex;
  justify-content: center;
  margin: 0;
  place-items: center;
}

a.card-link {
  text-decoration: none;
  color: rgb(255, 127, 8);
}

.btn {
  margin-left: 5px;
}
</style>
