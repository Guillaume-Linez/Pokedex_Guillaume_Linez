<template>
  <div class="container">
    <PokemonSearch />
    <PokemonDetail v-if="isShow"
    :pokemonURL="pokemon.url"
    @closeDetails="closeDetails"
    />
    <PokemonList 
    @showDetails="showDetails"
    />
  </div>
</template>

<script>
import PokemonDetail from "../components/PokemonDetail.vue";
import PokemonList from "../components/PokemonList.vue";
import PokemonSearch from "../components/PokemonSearch.vue";

export default {
  components: {
    PokemonDetail,
    PokemonList,
    PokemonSearch,
  },
  data:() => {
    return {
      pokemon: {},
      isShow: false
    }
  },
  methods: {
    showDetails(pokemon){
      this.isShow = true,
      this.pokemon = pokemon
    },
    closeDetails(){
      this.isShow = false
      this.pokemon = {}
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  //background: radial-gradient(#ffbf0b, #e20000);

  font-family: "Acme", arial;
  font-size: 1rem;
  font-weight: normal;
}

h1 {
  color: #efefef;
}
</style>