<template>
  <div id="app">
    <FontSelect></FontSelect>
  </div>
</template>

<script>
import FontSelect from './components/FontSelect.vue';

export default {
  components: {
    FontSelect
  },
}
</script>

<style>
  body {
    padding: 50px;
    background-color: #333;
  }

  p,
  h1 {
    color: #fff;
  }
</style>
