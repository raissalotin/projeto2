<script setup>
import{ref, computed} from 'vue'


const produtos = ref([
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90
    }
]
)

const carrinho =ref( {
    items: [],
    total: 0
})
let valorTotal = ref(0)

function adicionarCarrinho(produto) {
  carrinho.value.items.push({
    id: produto.id,
    nome: produto.nome,
    preco: produto.preco,
    quantidade: produto.quantidade,
    total: produto.preco * produto.quantidade
  });
  carrinho.value.total += produto.preco * produto.quantidade
}
function remover(index) {
    produtos.value.splice(index, 1)
  }

function incrementar(index) {
  produtos.value[index].quantidade++
  const pos = carrinho.value.items.indexOf(carrinho.value.items.find(c => c.id === produtos.value[index].id))
  if (pos != -1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total = ++carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
    carrinho.value.total += carrinho.value.items[pos].total

  }
}


function decrementar(index) {

if (produtos.value[index].quantidade > 0) {
  produtos.value[index].quantidade--
}
const pos = carrinho.value.items.indexOf(carrinho.value.items.find(c => c.id === produtos.value[index].id))
  if (pos != +1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total = --carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
    carrinho.value.total += carrinho.value.items[pos].total
  }
}
function limparCarrinho(){
carrinho.value.items = 0
carrinho.value.total = 0
}

</script>
<template>
  <div class="lista">
  <div class="linha"><div class="botaoCarrinho">
  <button carrinho type="button" class="btn">ver carrinho</button></div>
  <div class="modal" id="carrinho"></div>
  

  
  
  
  </div>
  <hr>
  <div class="linha"><div class="prodItem"></div></div>
  <ul>
    <div v-for="(item, index) in produtos">{{ item }}<div></div> <button @click="remover(index)">Remover</button>
    <button @click="incrementar(index)">adicionar </button></div>
  </ul>
 
   
  </div>
</template>