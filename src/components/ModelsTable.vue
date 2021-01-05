<template>
  <section id="models">
    <div class="card">
      <header class="card-header">
        Modelos
      </header>
      <main class="card-content">
        <template v-if="!isLoading">
          <table class="app-table">
            <tr>
              <th>Modelos</th>
            </tr>
            <tr v-for="model in models" :key="model.codigo">
              <td>
                {{ model.nome }}
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
  name: 'models-table',
  props: {
    selectedBrand: {
      type: String,
      required: true,
    },
  },
  watch: {
    selectedBrand() {
      this.fetchModels();
    }
  },
  data() {
    return {
      models: [],
      isLoading: false,
    };
  },
  methods: {
    fetchModels() {
      this.isLoading = true;
      axios.get(`https://parallelum.com.br/fipe/api/v1/carros/marcas/${this.selectedBrand}/modelos`)
        .then((res) => {
          this.models = res.data.modelos;
          this.isLoading = false;
        })
        .catch((err) => {
          alert(`Erro ao realizar fetch:\n ${err}`);
          this.isLoading = false;
        });
      this.scrollIntoTable();
    },
    scrollIntoTable() {
      let el = document.getElementById('models');
      el.scrollIntoView(false);
    },
  },
  mounted() {
    this.fetchModels();
  },
}
</script>

<style scoped>

</style>