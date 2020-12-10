<template>
<v-app>
  <div class="app">
    <Header/>
    <Card class="card"/>
  </div>
</v-app>
</template>

<script>
import Header from './components/Header';
import Card from './components/Card';

export default {
  name: 'App',

  components: {
    Header,
    Card
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
.card{
  margin-top: -470px;
}
</style>
