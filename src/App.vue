<template>
  <div id="app">
    <ContadorView/>
    <Contador titulo2="Contador 1" v-bind:inicio="20" :mostrar="true"/>
    <Contador titulo2="Contador 2" :inicio="4" :mostrar="false"/>
  </div>
</template>
 
<script>
import ContadorView from '../src/views/ContadorView.vue';
import Contador from '../src/components/Contador.vue';
export default {
  name: 'App',
  components: {
    ContadorView,
    Contador
  }
 
};
</script>
 
<style>
 
</style>