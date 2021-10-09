<template>
  <div id="app">
    <PokeAPI />
    <PokeApiLocations />
    <Crear />
    <Editar />
    <Listar />
  </div>
</template>

<script>
import PokeAPI from './components/PokeAPI.vue'
import PokeApiLocations from './components/PokeApiLocations.vue'
import Crear from './components/Crear.vue'
import Editar from './components/Editar.vue'
import Listar from './components/Listar.vue'

export default {
  name: 'App',
  components: {
    PokeAPI,
    PokeApiLocations,
    Crear,
    Editar,
    Listar
  }
}
</script>