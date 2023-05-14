<script setup>
 import { ref } from 'vue'

const item = ref([
   {
       id: 1,
       nome: 'Camiseta',

       descricao: 'Uma camiseta limda',
       preco: 49.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,


   },
   {
       id: 2,
       nome: 'Calça',

       descricao: 'Unma calsa glamurosa',
       preco: 99.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,

   },
   {
       id: 3,
       nome: 'Meia',

       descricao: 'do novo filme da barbi',
       preco: 9.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",

   },
   {
       id: 4,
       nome: 'Sapato',

       descricao: 'Crocs perfeito',
       preco: 199.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg" ,

   },
   {
       id: 5,
       nome: 'Boné',

       descricao: 'importado do presídio',
       preco: 29.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",

   },
   {
       id: 6,
       nome: 'Óculos',

       descricao: 'Óculos Adryan Óculos',
       preco: 99.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",

   },
   {
       id: 7,
       nome: 'Relógio',

       descricao: 'não é roubado',
       preco: 299.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",

   },
   {
       id: 8,
       nome: 'Bermuda',

       descricao: 'Uma bermuta boninta',
       preco: 79.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://pbs.twimg.com/profile_images/1640054291984424965/5WyzoEgy_400x400.jpg",

   },
   {
       id: 9,
       nome: 'Cueca',

       descricao: 'Proteção garantida',
       preco: 19.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem :"https://images7.memedroid.com/images/UPLOADED672/5eb5b3f19c9a8.jpeg" ,

   },
   {
       id: 10,
       nome: 'Meia',

       descricao: 'Meia de novo',
       preco: 9.99,
       quantidade: 0,
       valorTotal: 49.99,
       imagem : "https://images7.memedroid.com/images/UPLOADED672/5eb5b3f19c9a8.jpeg",

   }
   
])


 function incrementar(index) {
    carrinho.value[index].quantidade++
    carrinho.value[index].totalItem = (carrinho.value[index].preco * carrinho.value[index].quantidade).toFixed(2)
    calcularTotal()
  }
  function decrementar(index) {
    carrinho.value[index].quantidade--
    carrinho.value[index].totalItem = (carrinho.value[index].preco * carrinho.value[index].quantidade).toFixed(2)
    calcularTotal()
  }
  

  const carrinho = ref([])
function addCarrinho(item, index) {
  if(item.quantidade == 0){
  item.quantidade = 1
  carrinho.value.push({
    codigo: item.id,
    nome: item.nome,
    preco: item.preco,
    quantidade: item.quantidade,
    totalItem: item.preco
  })
  } 
  calcularTotal()
  
 
}
const valorTotal = ref(0)

  function calcularTotal() {
    valorTotal.value = 0
    for(let i in carrinho.value) {
    valorTotal.value += Number(carrinho.value[i].totalItem)
  }
  valorTotal.value = valorTotal.value.toFixed(2)
  }
function limpaCarrinho() {
  carrinho.value = []
  calcularTotal()
}
function remover(index) {
  carrinho.value[index].quantidade = 0
  carrinho.value.splice(index, 1)
  calcularTotal()
}

</script>

<template>
  <div class="greice">
  <img src="components/13235657_1117075674982087_6011802041793867339_o.jpg" alt="">

  <div class="abananga">
  <div class="collapse" id="navbarToggleExternalContent">
  <div class="bg-dark p-4">
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
        <div class="">
    <h1>Carrinho</h1> 
    <ul class="list-group">
      <li class="list-group-item" style="font-size: 20px;" v-for="(item, index) in carrinho" :key="index">{{ item.nome }} 
      <li class="list-group"> valor: R${{item.preco }}</li>
    <li class="list-group-item">Quantidade: {{ item.quantidade }}</li>
    <button class="btn btn-outline-success" id="remove" @click="incrementar(index)">gg</button>  
    <button  class="btn btn-outline-warning" id="remove" v-if="item.quantidade > 1" @click="decrementar(index)">ff</button>  
    <button class="btn btn-outline-danger" id="remove" @click="remover(index)">remover item</button>  
    <p class="letraTotal">Preço total: {{ (item.totalItem) }}</p>
    
   
      </li>

    </ul>
    <ul class="list-group">
    <li class="list-group-item"> Valor Total R${{ valorTotal }}</li>
  </ul>
    <button class="btn btn-primary" @click="limpaCarrinho()">limpar carrinho</button>
  </div>
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
  <img src="https://scontent.fjoi10-1.fna.fbcdn.net/v/t31.18172-8/13235657_1117075674982087_6011802041793867339_o.jpg?_nc_cat=103&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=0NaXfo85KHQAX_FnKrm&_nc_ht=scontent.fjoi10-1.fna&oh=00_AfCqNlBsA787d6PDGSSQhNwGVfH8cg_ioVthaPG2kd-MOA&oe=64875ED9" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ item.nome }}</h5>
    <p class="card-text"> {{  item.descricao  }}</p>
  </div>
  <ul class="list-group list-group-flush" >
    <li class="list-group-item">

  <p>Preço: R${{ item.preco }}</p></li> </ul>
  
  
  <div class="card-body">
    <a href="#" class="card-link">Card link</a>
    <button type="button" class="btn btn-primary" @click="addCarrinho(item)">Adicionar</button>

  </div>
  <ul class="list-group list-group-flush" >
    <li class="list-group-item">
  <p>Preço: R${{ item.preco }}</p>
    </li>
  </ul>
</div>
</div>

<ul>
    
</ul>
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
.list-group-item {
  margin: 5px;
  
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

.greice {
  width: 100%;
  height: 100%;
  background-image: url("components/13235657_1117075674982087_6011802041793867339_o.jpg");
}

p {
  margin-bottom: 0;
}

.letraTotal {
  margin-top: 10px;
}
</style>
