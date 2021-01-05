<template>
  <section>
    <div class="card">
      <header class="card-header">
        Marcas
      </header>
      <main class="card-content">
        <template v-if="!isLoading">
          <table class="app-table">
            <tr>
              <th>Marca</th>
              <th></th>
            </tr>
            <tr v-for="brand in brands" :key="brand.codigo">
              <td>
                {{ brand.nome }}
              </td>
              <td>
                <a class="flat-button" :class="{ 'active': selected === brand.codigo }" role="button" @click="selectBrand(brand.codigo)">
                  Ver modelos
                </a>  
              </td>
            </tr>
          </table>
        </template>
        <template v-else>
          Carregando conteúdo...
        </template>
      </main>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: 'brands-table',
  data() {
    return {
      brands: [],
      selected: null,
      isLoading: true,
    };
  },
  methods: {
    fetchBrands() {
      axios.get('https://parallelum.com.br/fipe/api/v1/carros/marcas')
        .then((res) => {
          this.brands = res.data;
          this.isLoading = false;
        })
        .catch((err) => {
          alert(`Erro ao realizar fetch:\n ${err}`);
          this.isLoading = false;
        });
    },
    selectBrand(id) {
      this.selected = id;
      this.$emit('update:selectedBrand', id);
    },
  },
  mounted() {
    this.fetchBrands();
  },
}
</script>

<style scoped>

</style>