<script setup>
import{ref} from 'vue'
const novoItem = ref('')
const listaCompras = ref(['arroz', 'batata', 'feijão'])
const produtos = [
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
//por nos produtos
function adicionar()
  {
    listaCompras.value,push(novoItem.value)
    novoItem.value = ''
}

//por no carrinho
function remover(index) {
    listaCompras.value.splice(index, 1)
  }

</script>
<template>

  <button @click="adicionar">Adicionar</button>
  <ul>
    <li v-for="item in listaCompras">{{ item }}</li>
  </ul>
 
  <ul>
    <li v-for="(item, index) in listaCompras">{{ item }} <button @click="remover(index)">Remover</button></li>
  </ul>
</template>