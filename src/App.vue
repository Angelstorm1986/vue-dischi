<template>
  <div id="app">
    <app-header/>
    <app-grid/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppGrid from './components/AppGrid.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppGrid
  }
}
</script>

<style lang="scss">
@import "./style/vars.scss";
@import "./style/general.scss";
</style>
