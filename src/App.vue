<template>
  <div id="app">
    <LicencePlate />
  </div>
</template>

<script>
import LicencePlate from './components/LicencePlate.vue';
export default {
  name: 'App',
  components: { LicencePlate },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
