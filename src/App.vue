<template>
  <div id="app">
    <PokeAPI />
    <PokeApiLocations />
  </div>
</template>

<script>
import PokeAPI from './components/PokeAPI.vue'
import PokeApiLocations from './components/PokeApiLocations.vue'


export default {
  name: 'App',
  components: {
    PokeAPI,
    PokeApiLocations
  }
}
</script>