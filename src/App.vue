<template>
  <div id="app">
    <Appbar />
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
  </div>
</template>

<script>
import Appbar from './components/Appbar';
import BrandsTable from './components/BrandsTable';
import ModelsTable from './components/ModelsTable';

export default {
  name: 'App',
  components: {
    Appbar,
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
