<template>
  <div class="relative">
    <label class="py-2 flex justify-end items-end mt-2 mb-4">
      <span class="font-bold text-gray-600 text-sm">{{ label }}</span>
      <input
        :class="[
          'w-4/6 ml-4 px-2 py-1 rounded-sm box-border border-2 border-transparent',
          { 'border-red-400': !!dangerMessage },
        ]"
        :value="value"
        v-bind="$attrs"
        @input="updateValue"
      />
    </label>
    <div
      class="w-4/6 text-red-400 text-sm absolute right-0 text-left -bottom-3 italic"
    >
      {{ dangerMessage }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'InputGroup',
  props: {
    dangerMessage: {
      type: String,
      default: '',
    },
    label: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      required: true,
    },
  },
  methods: {
    updateValue(e: any) {
      this.$emit('input', e.target.value)
    },
  },
})
</script>
