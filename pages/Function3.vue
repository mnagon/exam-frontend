<template>
  <div class="container mx-auto max-w-screen-sm">
    <p v-for="(arr, i) in testCase" :key="i">
      {{ arr }} //{{ getSecondMax(arr) }}
    </p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      testCase: [
        [],
        [1],
        [1, 2, 3],
        [1, 1],
        [1, 2, 3, 4, 5, 6],
        [1, 5, 3, 2, 5, 10],
        [100, 5, 3, 2, 99],
        [35, 5, 3, 2, 5, 100],
        [1, 5, 101, 2, 5, 10],
        [10, 10, 9],
      ],
    }
  },
  computed: {},
  methods: {
    getSecondMax(arr: number[]): any {
      const set = new Set(arr)
      const uniqueArr = [...set]
      if (uniqueArr.length < 1) {
        return null
      } else if (uniqueArr.length === 1) {
        return arr[0]
      } else {
        return uniqueArr.sort((a, b) => b - a)[1]
      }
    },
  },
})
</script>
