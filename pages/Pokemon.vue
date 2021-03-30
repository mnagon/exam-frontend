<template>
  <div class="w-full bg-indigo-200 px-5 py-6 text-center text-gray-600 mb-8">
    <span class="text-lg font-bold">Test fetch API</span>
    <div class="flex flex-wrap justify-start mt-8">
      <template v-if="!isLoading">
        <pokemon-card
          v-for="pokemon in pokemonList"
          :key="pokemon.id"
          :pokemon="pokemon"
        />
      </template>
      <template v-else>
        <pokemon-skeleton v-for="n in 104" :key="n" />
      </template>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
interface State {
  isLoading: boolean
  pokemonList: any[]
}
export default Vue.extend({
  data(): State {
    return {
      isLoading: true,
      pokemonList: [],
    }
  },
  async mounted(): Promise<void> {
    for (let i = 1; i < 105; i++) {
      const res = await this.fetchPokemon(i)
      this.pokemonList.push(res)
    }
    this.isLoading = false
  },
  methods: {
    async fetchPokemon(pokemonNumber: number): any {
      const pokemon = await this.$axios.$get(
        'https://pokeapi.co/api/v2/pokemon/' + pokemonNumber
      )
      return pokemon
    },
  },
})
</script>

<style></style>
