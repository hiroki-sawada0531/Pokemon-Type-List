<template>
  <div class="container">
    <div v-for="(pokemon, index) in pokemons" :key="index" class="constent">
      <div>{{ pokemon.name }}　{{ pokemon.types[0] }}, {{ pokemon.types[1] }}</div>
    </div>
  </div>
</template>

<script>
const axios = require('axios')
const url = 'https://raw.githubusercontent.com/kotofurumiya/pokemon_data/master/data/pokemon_data.json'

export default {
  asyncData({ params, error }) {
    return axios
    .get(url)
    .then((res) => {
      console.log(res.data)
      return { pokemons: res.data }
    })
    .catch((e) => {
      error({ pokemon: e.response.status, message: 'ERROR!!' })
    })
  }
}
</script>
<style>
.container {
  text-align: center;
  margin: 50px auto;
  padding: 0;
}

.constent {
  margin: 0 auto;
}
</style>
