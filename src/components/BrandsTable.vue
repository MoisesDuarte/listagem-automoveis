<template>
  <section>
    <h1>Veículos</h1>

    <div class="card">
      <header class="card-header">
        Marcas
      </header>
      <main class="card-content">
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
              <a class="flat-button" role="button" @click="selectBrand(brand.codigo)">
                Ver modelos
              </a>  
            </td>
          </tr>
        </table>
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
    };
  },
  methods: {
    fetchBrands() {
      axios.get('https://parallelum.com.br/fipe/api/v1/carros/marcas')
        .then((res) => {
          console.info(res);
          this.brands = res.data;
        });
    },
    selectBrand(id) {
      this.$emit('select-brand', id);
    },
  },
  mounted() {
    this.fetchBrands();
  },
}
</script>

<style scoped>
h1 {
  font-size: 1.5rem;
}
</style>