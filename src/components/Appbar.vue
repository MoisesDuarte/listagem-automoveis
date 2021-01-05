<template>
  <nav class="appbar">
    <div class="logo">
      Navita
    </div>
  </nav>
</template>

<script>
export default {
  name: 'appbar',
}
</script>

<style scoped>
.appbar {
  background: #ffffff;
  padding: 1em;
  font-size: 1.25rem;
  -webkit-box-shadow: 0px 8px 10px 0px rgba(58, 59, 69, .15);
  -moz-box-shadow: 0px 8px 10px 0px rgba(58, 59, 69, .15);
  box-shadow: 0px 8px 10px 0px rgba(58, 59, 69, .15);
}

.logo {
  color: var(--color-primary);
  font-weight: 700;
}
</style>