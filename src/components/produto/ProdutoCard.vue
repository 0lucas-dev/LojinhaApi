<script lang="ts">
import { capitalize } from 'vue';

export default {
  name: 'ProdutoCard',
  props: {
    produto: Object
  },
  computed: {
    capitalize() {
      if (this.produto) {
        let title = this.produto.title
        return title.charAt(0).toUpperCase() + title.slice(1)
      }
    },
    pegarImagem() {
      if (this.produto && this.produto.images && this.produto.images.length > 0) {
        return this.produto.images[0]
      } else {
        return ''
      }
    }
  },
  methods: {
    verDetalhes() {
      if (this.produto) {
        let id = this.produto.id
        this.$router.push({ name: 'produtos-detalhes', params: { id } })
      }
    }
  }
}
</script>

<template>
  <b-card :title="capitalize" class="mb-3" body-class="text-center card-pokemon">
    <b-img :src="pegarImagem" style="width: 100px; height: 100px;" class="mb-2" />
    <b-button variant="primary" @click="verDetalhes">
      Ver Detalhes
    </b-button>
  </b-card>
</template>
<style>
.card-pokemon {
  width: 250px;
  height: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
