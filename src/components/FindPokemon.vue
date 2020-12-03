
<template>
    <div>
        <h4>{{pokemon.name}}</h4>
        <p>Weight: {{pokemon.weight}}</p>
        <p>Height: {{pokemon.height}}</p>
        
        <button @click="returnHome">Voltar</button>
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
            this.getDados(id);
        },
        getDados(id){
            axios
            .get(`http://127.0.0.1:8000/api/pokemon/buscar/${id}`)
            .then(response => (this.pokemon = response.data))
            
        },
        returnHome(){
            this.$router.push(`/`)
        }
    },
}
</script>