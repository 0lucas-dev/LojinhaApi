<script lang="ts">
import { capitalize } from 'vue'

export default {
  name: 'ProdutoCard',
  props: {
    produto: Object,
  },
  computed: {
    capitalize() {
      if (this.produto) {
        let title = this.produto.title
        return title.charAt(0).toUpperCase() + title.slice(1)
      }
      return ''
    },
    pegarImagem() {
      return this.produto.images[0]
    },
  },
  methods: {
    preco(){
      return this.produto.price
    },
    verDetalhes() {
      if (this.produto) {
        let id = this.produto.id
        this.$router.push({ name: 'produto-detalhes', params: { id } })
      }
    },
  },
}
</script>

<template>
  <div class="card" style="width: 22rem;">
    <img :src="pegarImagem" class="card-img-top" alt="imagem-produto">
    <div class="details card-body d-flex flex-column align-items-center ">
      <h5 class="card-title text-white fw-bold">{{ capitalize }}</h5>
      <p class="card-text text-white fw-bold"><b>Preço: R$ </b>{{ preco() }}</p>
      <button class="btn btn-primary w-100 mb-2" @click="verDetalhes"> Ver Detalhes </button>
      <button class="btn btn-success w-100 mb-2"> Adicionar ao Carrinho </button>
    </div>
  </div>
</template>
<style>
.card-produto {
  width: 250px;
  height: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.details{
  color: #ffffff;
  background-color: #221145;
}
</style>
