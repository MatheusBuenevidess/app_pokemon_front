
<template>
    <div>
        <p>{{pokemon}}</p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'FindPokemons',
    data () {
        return {
        pokemon: null
        }
    },
  mounted () {
    this.getIdPokemon()
  },
  methods: {
      getIdPokemon(){
          const {id} = this.$route.params;
          console.log(id);
          this.getDados(id);
      },
      getDados(id){
           axios
            .get(`http://127.0.0.1:8000/api/pokemon/buscar/${id}`)//Adicionar o ID do Pokemon
            .then(response => (this.pokemon = response))
      }
  },
}
</script>