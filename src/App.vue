<template>
  <div id="app">
    <img class="poke_logo" src="@/assets/pokemon_logo.png" alt="pokemon logo" />
    <form>
      <label for="txt_nombre"><span>Nombre: </span> </label>
      <input type="text" name="txt_nombre" id="txt_nombre" v-model="nombrePokemon" />
      <button type="submit" @click.prevent="busquedaPokemon">Buscar</button>
    </form>
    <Pokemon :detallePokemon="detallePokemon" />
    
  </div>
</template>

<script>
import Pokemon from "@/components/Pokemon";
import { getPokemon } from "@/PokeApi";
export default {
  name: "App",
  components: {
    Pokemon,
  },
  data() {
    return {
      nombrePokemon: "",
      detallePokemon: {},
    };
  },
  methods: {
    async busquedaPokemon() {
      const { nombrePokemon } = this;
      this.detallePokemon = await getPokemon(nombrePokemon);
    },
  },
  async created() {
    this.detallePokemon = await getPokemon("pikachu");
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  }
#app {
 
  background:rgba(83, 77, 77, 0.315);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
 ;
}

.poke_logo {
  width: 25%;
  -o-object-fit: cover;
  object-fit: cover;
  height: 25%;
}

span{
  font-size:30px;
}

img{
  padding-bottom:40px;
}
</style>
