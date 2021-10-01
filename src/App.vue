<template>
  <div id="app">
    <PokeAPI />
  </div>
</template>

<script>
import PokeAPI from './components/PokeAPI.vue'

export default {
  name: 'App',
  components: {
    PokeAPI
  }
}
</script>