
<template>
    <div>
        <div v-for="(pokemon,index) in pokemons['data']" :key="pokemon.name">
            <div class="">
                <p>{{pokemon.name}}</p>
                <button @click="detailsPokemon(index+1)">Botao</button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'ListPokemons',
    data () {
        return {
        pokemons: null
        }
    },
  mounted () {
    axios
      .get('http://127.0.0.1:8000/api/pokemon/buscar')
      .then(response => (this.pokemons = response)) // passar methods
  },
  methods: {
      detailsPokemon(id){
          this.$router.push(`/detalhes/${id}`)
      }
  },
}
</script>