<script lang="ts">
import axios from 'axios';
import ProdutoCard from '../components/produto/ProdutoCard.vue';

export default {
  name: 'ListView',
  components: {
    ProdutoCard
  },
  data() {
    return {
      produtos: [],
      total_produtos: 0,
      limit: 20,
      pagina_atual: 1,
      offset: 0,
      busca: ''
    }
  },
  mounted() {
    console.log("Componente montado")
    this.listarProdutos()
  },
  computed: {
    produtosFiltrados() {
      return this.produtos.filter(produto => produto.title.includes(this.busca.toLowerCase()))
    }
  },
  watch: {
    pagina_atual(novo_valor) {
      this.offset = (novo_valor - 1) * this.limit
      this.listarProdutos()
    }
  },
  methods: {
    async listarProdutos() {
      try {
        const resposta = await axios.get(`https://dummyjson.com/products?limit=${this.limit}&skip=${this.offset}`)
        this.produtos = resposta.data.products
        this.total_produtos = resposta.data.total
      } catch (erro) {
        console.error(erro)
      }
    }
  }

}
</script>

<template>
  <div class="d-flex container align-items-center flex-column">
    <b-form-input v-model="busca" class="w-50 mb-3" placeholder="Busque pelo nome do produto" />
    <b-row>
    <b-col class="mb-3" v-for="produto in produtosFiltrados" :key="produto.id">
      <ProdutoCard :produto="produto"></ProdutoCard>
    </b-col>
    <b-pagination class="mt-3" v-model="pagina_atual" :total-rows="total_produtos" :per-page="limit" />
  </b-row>
  </div>
</template>
