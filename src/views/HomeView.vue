<template>
  <div class="w-full flex justify-center">
    <input type="text" placeholder="Enter Pokemon here" class="mt-10 p-2 border-blue-500 border-2 outline-none rounded-lg" v-model="text"/>
  </div>
  <div class="max-h-[60vh] mt-10 p-4 flex flex-wrap justify-center overflow-y-auto custom-scrollbar">
    <div class="ml-4 text-2xl text-blue-500" v-for="(pokemon, idx) in filteredPokemon" :key="idx">
      <router-link :to="`/about/${pokemon.name}`">{{ pokemon.name }}</router-link>
    </div>
  </div>
</template>

<script>

import { reactive, toRefs, computed} from 'vue';

export default {
  name: 'HomeView',
  setup() {
    const state = reactive({
      pokemons: [],
      urlIdLookup: {},
      text: "",
      filteredPokemon: computed(() => updatePokemon())
    })

    function updatePokemon() {
      if (!state.text.trim()) return []
      return state.pokemons.filter((pokemon) => pokemon.name.includes(state.text))
    }

    
    fetch("https://pokeapi.co/api/v2/pokemon?limit=10000&offset=0")
      .then((res) => res.json())
      .then((data) => {
        state.pokemons = data.results;
        state.urlIdLookup = data.results.reduce((acc, cur, idx) =>
          acc = { ...acc, [cur.name]: idx + 1 }
        ,{})
      })

      return {...toRefs(state)}
  }
}
</script>
