<template>
  
  <MenuComponents />
  <ProductoSeleccionadoComponents />
  <ProductosComponents/>
  <PieComponents footerColor="slategrey"/>
  
</template>

<script>
import MenuComponents from './components/MenuComponents.vue'
import PieComponents from './components/PieComponents.vue'
import ProductoSeleccionadoComponents from './components/ProductoSeleccionadoComponents.vue'
import ProductosComponents from './components/ProductosComponents.vue'


export default {
  name: 'App',
  components: {
    MenuComponents,
    ProductoSeleccionadoComponents,
    ProductosComponents,
    PieComponents
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
