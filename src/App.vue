<script setup>
import {reactive, ref} from 'vue'

const titulo = ref('Hello')
const produto= reactive({
  nome: '',
  preco: 0,
  quantidade: 10,
  categorias: []
})

const mostraResultado= ref(false)

function formatarPreco(preco){
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}

</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="contanier">
    <div class="formulario">
      <h2>Formulário</h2>
      <input type="text" v-model="titulo"/>
      <form @submit.prevent="mostraResultado = !mostraResultado">
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome" required/>
      </div>

      <div class="row">
        <label for="">Preço:</label>
        <input type="number" v-model="produto.preco"/>
      </div>

      <div class="row">
        <label for="">Quantidade:</label>
        <input type="number" v-model="produto.quantidade"/>
      </div>

      <button type="submit">Mostrar</button>
      </form>
    </div>

    <div v-if="mostraResultado" class="resultado"> 
      <h2>Resultado</h2> 
      <p>Nome: {{ produto.nome }}</p> 
      <p>Preço: {{ formatarPreco(produto.preco) }}</p> 
      <p>Quantidade: {{ produto.quantidade }}</p> 
      <p>Categorias: {{ produto.categorias }}</p> 
      <p>{{ mostraResultado }}</p>
    </div>
    
  </div>
</template>

<style scoped>

.contanier{
display: flex;
flex-direction: row;
justify-content: center;
gap: 1.5rom;
width: 100w;
}

.formulario,
.resultado {
  background-color:rgb(255, 255, 255);
  width: 45%;
  border-radius: 10px;
  padding: 10px;
}

.formulario{
  background-color:rgb(201, 181, 70);
}

.formulario.row{
  margin: 10px auto;
  width: 70%;
  display: flex;
  justify-content: space-between;
}

.resultado{
  background-color:rgb(224, 131, 236);
}
</style>