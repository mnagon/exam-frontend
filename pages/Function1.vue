<template>
  <div class="container mx-auto max-w-screen-sm">
    <div
      v-for="(products, i) in noEditablePriceSubProjects"
      :key="i"
      class="mb-4"
    >
      <p>name: {{ products.name }}</p>
      <p>totalSubProductWeight: {{ products.totalSubProductWeight }}</p>
      <hr />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import data from '~/static/exam-data.json'

export default Vue.extend({
  asyncData() {
    return { data }
  },
  computed: {
    noEditablePriceProducts(this: any) {
      return this.data.filter((e: any) => !e.is_editable_price)
    },
    noEditablePriceSubProjects() {
      return [
        ...this.noEditablePriceProducts.reduce(
          (a: any[], b: any) => a.concat(b.products),
          []
        ),
      ].map((e) => ({
        name: e.name,
        totalSubProductWeight: e.amount * e.weight,
      }))
    },
  },
})
</script>
