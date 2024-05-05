<template>
  <div id="app">
    <Quote />
  </div>
</template>

<script>
import Quote from './components/Quote.vue';

export default {
  name: 'App',
  components: {
    Quote
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
