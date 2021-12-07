<template>
  <div>
    <h1>PokeGuía</h1>
    <form>
      <label for="">Nombre: </label>
      <input type="text" v-model="pokemon.name" />
      <input type="submit" @click.prevent="fetchPokemon" />
    </form>
    <br />
    <section>
      <img :src="img" alt="img" />
      <h4>Movimientos</h4>
      <p v-for=" move in movimientos" :key="move">{{ move }}</p>
      <br />
      <h4>Habilidades</h4>
      <p v-for="habilidad in habilidades " :key="habilidad">{{ habilidad }}</p>
    </section>
  </div>
</template>

<script>
export default {
  name: "component-poke",
  // props: {},
  data: function () {
    return {
      pokemon: {
        name: `ditto`,
        move: [],
        abilities: [],
        image: ` `,
      },
    };
  },
  computed: {
    img() {
      return this.pokemon.image;
    },
    movimientos() {
        console.log(this.pokemon)
        if (this.pokemon.move){
           return this.pokemon.move.map((move)=>{
          console.log(move.move.name)
          return move.move.name
      }); 
        }
        return []
      
    },
    habilidades() {
        if (this.pokemon.abilities){
            return this.pokemon.abilities.map((abilitie)=>{
                console.log(abilitie.ability.name)
                return abilitie.ability.name
            });
        }
      return []
    },
  },
  methods: {
    fetchPokemon() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
        .then((response) => response.json())
        .then((json) => {
          console.log(json,"fetchPoke");
          this.pokemon.abilities = json.abilities
          this.pokemon.name = json.name
          this.pokemon.move = json.moves
          this.pokemon.image = json.sprites.front_default
          
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  created() {
    this.fetchPokemon();
  },
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>