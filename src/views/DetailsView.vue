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
  <div class="container d-flex flex-column text-center">
    <b-card v-if="produto">
      <h3>{{ capitalizar }}</h3>
      <b-img class="img-produto mb-3" :src="pegarImagem" />
      <p><b>preço: R$</b>{{ produto.price }}</p>
      <p><b>Descrição: </b>{{ produto.description }}</p>
      <b-button variant="secondary" class="mt-2" @click="$router.back()"> Voltar </b-button>
    </b-card>
  </div>
</template>
<style>
.img-produto {
  width: 200px;
}
</style>
