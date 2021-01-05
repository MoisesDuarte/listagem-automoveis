<template>
  <div id="app">
    <Appbar />
    <main class="ma-2">
      <BrandsTable/>
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
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300;400;500;600;700&display=swap');

:root {
  --color-primary: #25C98E;
  --color-grey: #f7f8fb;
  --color-blue: #4F73DF;
  --text-black: #333333;
}

body {
  background: var(--color-grey);
  color: var(--text-black);
  margin: 0;
  padding: 0;
  font-family: 'Comfortaa', cursive;
}

.ma-2 {
  margin: 2em;
}
</style>
