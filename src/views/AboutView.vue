<template>
  <div class="w-full flex items-center justify-center">
    <div v-if="pokemon" class="w-auto p-6 min-w-fit bg-cyan-200 mt-4 shadow-2xl flex justify-center flex-col items-center rounded-[24px]">
      <h3 class="text-2xl text-green-900 font-bold uppercase p-2">{{ pokemon.name }}</h3>
      <div class="flex justify-center">
        <img v-if="pokemon.sprites.front_shiny" class="w-48" :src="pokemon.sprites.front_shiny" alt="">
        <img v-if="pokemon.sprites.back_shiny" class="w-48" :src="pokemon.sprites.back_shiny" alt="">
      </div>
      <h3 class="text-orange-600 text-xl">Types</h3>
      <div v-for="(type, idx) in pokemon.types" :key="idx">
        <h5 class="text-blue-900">{{ type.type.name }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import { useRoute } from "vue-router";

export default {
  

  setup() {
    const route = useRoute();

    const state = reactive({ pokemon: null })

    fetch(`https://pokeapi.co/api/v2/pokemon/${route.params.slug}/`)
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        state.pokemon = data;
      })

    return {...toRefs(state)}
  }
}
</script>