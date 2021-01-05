<template>
  <div id="app">
    <Appbar />
    <main class="container">
      <BrandsTable @select-brand="selectedBrand = $event" />
    </main>
  </div>
</template>

<script>
import Appbar from './components/Appbar';
import BrandsTable from './components/BrandsTable';

export default {
  name: 'App',
  components: {
    Appbar,
    BrandsTable,
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
</style>
