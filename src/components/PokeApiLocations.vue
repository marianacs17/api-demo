<template>
  <div>
    <div>
      <b-form>
        <b-form-group id="input-group-3" label="Selecciona la ubicacion" label-for="input-3">
          <b-form-select
              id="input-3"
              v-model="selectedLocation"
              :options="pokemons"
              required
              @change="getPokemonDetail"
          ></b-form-select>
        </b-form-group>
      </b-form>
      <b-card v-if="selectedLocation"
              class="mt-3"
              :header="'Ubicacion seleccionada: ' + selectedLocation"
      >
        <pre class="m-0">{{  }}</pre>
        <b-card-body>
          <b-button v-b-toggle.collapse-1 variant="primary">Habilidades</b-button>
          <b-collapse id="collapse-1" class="mt-2">
            <b-card>
                <ul>
                    <li :key="index" v-for="(item,index) in pokemonDetail.locations">
                        {{item.ability.name}}
                    </li>
                </ul>
            </b-card>
          </b-collapse>
        </b-card-body>
      </b-card>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
const BASE_URL = 'https://pokeapi.co/api/v2/location/'
export default {
  data() {
    return {
      selectedLocation: null,
      pokemons: [],
      pokemonDetail: {}
    }
  },
  mounted() {
    this.getFirstTenPokemons()
  },
  methods: {
    getFirstTenPokemons () {
      const resource = 'pokemon?limit=10'
      axios.get(BASE_URL + resource)
          .then(res => {
            this.pokemons = res.data.results.map(pokemon => pokemon.name)
          })
          .catch(err => {
            console.log(err)
          })
    },
    getPokemonDetail () {
      const resource = 'location/' + this.selectedLocation
      axios.get(BASE_URL + resource)
          .then(res => {
            this.pokemonDetail = res.data
          })
          .catch(err => {
            console.log(err)
          })
    }
  }
}
</script>