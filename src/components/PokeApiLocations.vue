<template>
  <div>
    <div>
      <b-form>
        <b-form-group id="input-group-3" label="Selecciona la ubicacion" label-for="input-3">
          <b-form-select
              id="input-3"
              v-model="selectedLocation"
              :options="locations"
              required
              @change="getgameIndices"
          ></b-form-select>
        </b-form-group>
      </b-form>
      <b-card v-if="selectedLocation"
              class="mt-3"
              :header="'Ubicacion seleccionada: ' + selectedLocation"
      >
        <b-card-body>
          <b-button v-b-toggle.collapse-2 variant="primary">Locaciones</b-button>
          <b-collapse id="collapse-2" class="mt-2">
            <b-card>
                <ul>
                    <li> {{game_indices.name}}
                    </li>
                </ul>
            </b-card>
          </b-collapse>
          <b-button v-b-toggle.collapse-3 variant="primary">Names</b-button>
          <b-collapse id="collapse-3" class="mt-2">
            <b-card>
                <ul>
                    <li :key="index" v-for="(item,index) in game_indices.names">
                        {{item.language.name}}
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
const BASE_URL = 'https://pokeapi.co/api/v2/'
export default {
  data() {
    return {
      selectedLocation: null,
      locations: [],
      game_indices: {}
    }
  },
  mounted() {
    this.getFirstTenLocations()
  },
  methods: {
    getFirstTenLocations () {
      const resource = 'location?limit=10'
      axios.get(BASE_URL + resource)
          .then(res => {
            this.locations = res.data.results.map(location => location.name)
          })
          .catch(err => {
            console.log(err)
          })
    },
    getgameIndices () {
      const resource = 'location/' + this.selectedLocation
      axios.get(BASE_URL + resource)
          .then(res => {
            this.game_indices = res.data
          })
          .catch(err => {
            console.log(err)
          })
    }
  }
}
</script>