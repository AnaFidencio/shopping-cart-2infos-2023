<script setup>
import MButton from './MButton.vue';
import CartPlus from 'vue-material-design-icons/CartPlus.vue'
import ShareVariant from 'vue-material-design-icons/ShareVariant.vue'
const props = defineProps({
  livro: Object
})

const emit = defineEmits(['adicionarAoCarrinho'])

function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}
</script>
<template>
  <div class="card-livro">
    <div class="card-info-livro">
      <div class="wrap-livro">
        <img :src="props.livro.img" alt="Capa do livro" class="capa-livro" />
      </div>
      <p class="titulo-livro">{{ props.livro.title }}</p>
      <p class="autor-livro">{{ props.livro.author }}</p>
      <p class="preco-livro">{{ formatarPreco(props.livro.price) }}</p>
    </div>
    <div class="card-buttons-livros">
      <m-button  class="secundario" @click="emit('adicionarAoCarrinho', props.livro)">
        <cart-plus /></m-button>
        <m-button class="sucesso"> <share-variant /> </m-button>
      
    </div>
  </div>
</template>
<style scoped> .wrap-livro {
   display: flex;
   justify-content: center;
   align-items: center;
   background-color: rgb(255, 255, 255);
   border-radius: 10px;
   width: 180px;
   height: 270px;
 }

 .capa-livro {
   width: 90%;
   max-height: 100%;
 }

 .card-livro p {
   margin: 0;
 }

 .card-livro .titulo-livro {
   font-weight: bold;
   margin-bottom: 5px;
 }

 .card-livro {
   margin: 5px 10px;
   padding: 10px;
   background-color: rgb(160, 204, 221);
   border-radius: 10px;
   width: 180px;
   display: flex;
   flex-direction: column;
   justify-content: space-between;
 }
</style>