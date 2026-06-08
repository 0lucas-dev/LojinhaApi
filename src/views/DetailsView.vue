<script lang="ts">
import { useRoute } from 'vue-router'
import axios from 'axios'
import { capitalize } from 'vue'

export default {
  name: 'DetailsView',
  data() {
    return {
      produto: null,
      id: null,
    }
  },
  mounted() {
    this.id = this.$route.params.id
    this.buscarDetalhes()
  },
  computed: {
    capitalizar() {
      return capitalize(this.produto.title)
    },
    pegarImagem() {
      return this.produto.images[0]
    },
  },
  methods: {
    preco() {
      return this.produto.price
    },
    async buscarDetalhes() {
      try {
        const resposta = await axios.get(`https://dummyjson.com/products/${this.id}`)
        this.produto = resposta.data
      } catch (erro) {
        console.error(erro)
      }
    },
  },
}
</script>

<template>

    <div
      v-if="produto"
      class="container d-flex flex-column text-center card"
      style="max-width: 900px"
    >
      <div class="row g-0">
        <div class="col-md-4">
          <img :src="pegarImagem" class="img-fluid rounded-start" alt="imagem-produto" />
        </div>

        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title fw-bold fs-2">{{ capitalizar }}</h5>
            <p class="card-text fw-semibold fs-5">{{ produto.description }}</p>
            <p class="card-text fw-bold fs-5">
              <small class="text-body-secondary"><b>Preço: R$ </b>{{ preco() }}</small>
            </p>
          </div>
        </div>
      </div>
      <b-button variant="primary" class="mt-2"> Adicionar ao Carrinho </b-button>
      <b-button variant="success" class="mt-2"> Comprar </b-button>
      <b-button variant="secondary" class="mt-2 mb-2" @click="$router.back()"> Voltar </b-button>
    </div>

</template>
<style>
.img-produto {
  width: 200px;
}
.card{
  margin: 10px;
}
</style>
