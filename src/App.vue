<template>
  <div id="app">
    <AppBar />
    <main class="container">
      <h1>Veículos</h1>
      <BrandsTable 
        :selectedBrand.sync="selectedBrand" 
      />
      <ModelsTable 
        v-if="selectedBrand" 
        :selectedBrand="selectedBrand"
        class="mt-2"
      />
    </main>
    <AppFooter />
  </div>
</template>

<script>
import AppBar from './components/AppBar';
import AppFooter from './components/AppFooter';
import BrandsTable from './components/BrandsTable';
import ModelsTable from './components/ModelsTable';

export default {
  name: 'App',
  components: {
    AppBar,
    AppFooter,
    BrandsTable,
    ModelsTable,
  },
  data() {
    return {
      selectedBrand: null,
    };
  },
}
</script>

<style>
.container {
  margin: 2em;
}

.mt-2 {
  margin-top: 2rem;
}
</style>
