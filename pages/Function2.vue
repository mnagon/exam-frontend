<template>
  <div class="container mx-auto max-w-screen-sm">
    <p>{{ date }}</p>
    <p>{{ firstFormat }}</p>
    <p>{{ thaiFormat }}</p>
    <p>{{ dayOfMonth }}</p>
    <p>{{ quater }}</p>
    <p>{{ timeStamp }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import moment from 'moment'
export default Vue.extend({
  data() {
    return {
      date: '2020-08-10T14:54:52+07:00',
    }
  },
  computed: {
    firstFormat() {
      return moment(new Date(this.date)).format('l h:mm')
    },
    thaiFormat() {
      return moment(new Date(this.date)).lang('th').format('LL')
    },
    dayOfMonth() {
      return moment(new Date(this.date)).daysInMonth()
    },
    quater() {
      return moment(new Date(this.date)).quarter()
    },
    timeStamp() {
      return moment(new Date(this.date)).unix()
    },
  },
})
</script>
