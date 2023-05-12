<script setup>
 import { ref } from 'vue'

const item = ref([
   {
       id: 1,
       nome: 'Camiseta',
       descricao: 'Uma camiseta limda',
       preco: 49.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,

   },
   {
       id: 2,
       nome: 'Calça',
       descricao: 'Unma calsa glamurosa',
       preco: 99.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,
   },
   {
       id: 3,
       nome: 'Meia',
       descricao: 'do novo filme da barbi',
       preco: 9.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",
   },
   {
       id: 4,
       nome: 'Sapato',
       descricao: 'Crocs perfeito',
       preco: 199.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,
   },
   {
       id: 5,
       nome: 'Boné',
       descricao: 'importado do presídio',
       preco: 29.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",
   },
   {
       id: 6,
       nome: 'Óculos',
       descricao: 'Óculos Adryan Óculos',
       preco: 99.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",
   },
   {
       id: 7,
       nome: 'Relógio',
       descricao: 'não é roubado',
       preco: 299.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",
   },
   {
       id: 8,
       nome: 'Bermuda',
       descricao: 'Uma bermuta boninta',
       preco: 79.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",
   },
   {
       id: 9,
       nome: 'Cueca',
       descricao: 'Proteção garantida',
       preco: 19.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem :"https://images7.memedroid.com/images/UPLOADED672/5eb5b3f19c9a8.jpeg" ,
   },
   {
       id: 10,
       nome: 'Meia',
       descricao: 'Meia de novo',
       preco: 9.90,
       quantidade: 0,
       valorTotal: 49.90,
       imagem : "https://images7.memedroid.com/images/UPLOADED672/5eb5b3f19c9a8.jpeg",
   }
   
])

 function incrementar(index) {
    item.value[index].quantidade++
  }
  function descrementar(index) {
    item.value[index].quantidade--
  }
  let valortotal = ref(0)

  const carrinho = ref([])
function addCarrinho(item) {
  carrinho.value.push({
    codigo: item.id,
    nome: item.nome,
    preco: item.preco,
    quantidade: item.quantidade,
    totalItem: item.preco * item.quantidade
  })
  totalValor()
  item.quantidade = 1
}
function totalValor(){
  for (let contador = 0; contador < carrinho.value.length; contador++) {
    valortotal.value = valortotal.value + carrinho.value[contador].totalItem  
  }
}
function limpaCarrinho() {
  carrinho.value = []
}
function remover(index) {
  carrinho.value.splice(index, 1)
}
</script>

<template>
  <div class="collapse" id="navbarToggleExternalContent">
  <div class="bg-dark p-4">
    <button class="btn btn-outline-success me-2" type="button">Carrinho</button>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
  Carrinho
</button>

<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">Carrinho</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        Informações aqui gabriel
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
        <button type="button" class="btn btn-primary">Adicionar</button>
      </div>
    </div>
  </div>
</div>
  </div>
</div>
<nav class="navbar navbar-dark bg-dark">
  <div class="container-fluid">
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarToggleExternalContent" aria-controls="navbarToggleExternalContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
  </div>
</nav>
  <div class="row">
 <div class="card" style="width: 15rem;" v-for="(item, index) in item" :key="item.id">
  <img src="{{ item.imagem }}" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ item.nome }}</h5>
    <p class="card-text"> {{  item.descricao  }}</p>
  </div>
  <ul class="list-group list-group-flush" >
    <li class="list-group-item">
  <p>Preço: R${{ item.preco }}</p></li> </ul>
  
  
  <div class="card-body">
    <a href="#" class="card-link">Card link</a>
    <button type="button" class="btn btn-primary" @click="addCarrinho(index)">Adicionar</button>
  </div>
  <li v-for="item in carrinhos">
        <p>Item: {{ item.name }}</p>

        <p>Preco: {{ item.price }}</p>
        <p>ID: {{ item.id }}</p>
    </li>
  
</div>
</div>
<ul>
    <div class="">
    <h1>Carrinho</h1> 
    <ul>
      <li v-for="(item, index) in carrinho" :key="index">{{ item.nome }} 
      <p> valor: {{(item.preco) }} Preço</p>
    <p>Quant: {{ item.quantidade }}</p>
    <button id="remove" @click="remover(index)">remover item</button>  
    <p class="letraTotal">Preço total: {{ (item.totalItem) }}</p>
    
   
      </li>
    </ul>
    <button @click="limpaCarrinho()">limpar carrinho</button>
  </div>
</ul>

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
  width: 15rem;
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

.bg-dark {
  border-radius: 10px;
  
}
.card[data-v-7a7a37b1] {
  width: 15rem;
    display: flex;
    margin: 5px;
    justify-content: center;
    align-items: center;
    border-style: solid;
    border-radius: 20px;
    border-color: #868686;
    border-width: 3px;
}
</style>
