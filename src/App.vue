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
  
  function incrementar(index) {
    listaCompras.value[index].quantidade++
  } <button @click="incrementar(index)">Incrementar</button>

  function decrementar(index) {
    listaCompras.value[index].quantidade--
  } <button v-if="item.quantidade > 1" @click="decrementar(index)">Decrementar</button>

  function remover(index) {
    listaCompras.value.splice(index, 1)
  } <button @click="remover(index)">Remover</button>

</script>

<template>
<div v-for="(item) in produtos" :key="item.id">
  <p>Nome: {{ item.nome }}</p>
  <p>Preço: {{ item.preco }}</p>
</div>

</template>

<style scoped>

</style>
