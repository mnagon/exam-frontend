<template>
  <div class="w-1/6 px-6 mb-8">
    <img
      class="max-w-full max-h-20 mx-auto"
      :src="pokemon.sprites.front_default"
    />
    <div
      class="bg-black text-white w-full flex items-center justify-center rounded text-xs"
    >
      {{ pokemon.name }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue'
export default Vue.extend({
  props: {
    pokemon: {
      type: Object as PropType<any>,
    },
  },
})
</script>
