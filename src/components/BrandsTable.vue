<template>
  <section>
    <h1>Veículos</h1>

    <div class="card">
      <header class="card-header">
        Marcas
      </header>
      <main class="card-content">
        <table class="brands-table">
          <tr>
            <th>Marca</th>
            <th></th>
          </tr>
          <tr v-for="brand in brands" :key="brand.codigo">
            <td>
              {{ brand.nome }}
            </td>
            <td>
              <a role="button">Ver modelos</a>  
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

/* Card Styling */
.card {
  border: 1px solid #E3E6F0;
  border-radius: 6px;
  background: #ffffff;
  box-shadow: 0px 0px 20px 0px rgba(58, 59, 69, .15);
}

.card-header {
  border-bottom: 1px solid #E3E6F0;
  border-top-left-radius: inherit;
  border-top-right-radius: inherit;
  background: #F8F9FC;
  padding: 1.5rem;
  font-weight: 700;
  color: var(--color-blue);
}

.card-content {
  border-bottom-left-radius: inherit;
  border-bottom-right-radius: inherit;
  background: #ffffff;
  padding: 1.5rem;
  padding-top: 2em;
  max-height: 25em;
  overflow-y: scroll;
}

/* Table Styling */
.brands-table {
  border-collapse: collapse;
  width: 100%;
}

.brands-table tr {
  border-bottom: 1px solid #E3E6F0;
}

.brands-table tr:first-child {
  border-top: 1px solid #E3E6F0;
  border-bottom: 2px solid #E3E6F0;
}

.brands-table th, td {
  text-align: left;
  padding: 1rem;
}
</style>