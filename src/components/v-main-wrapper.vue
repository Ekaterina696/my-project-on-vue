<template>
    <div class="v-main-wrapper">
      <router-view></router-view>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'v-main-wrapper',
  computed: {
    ...mapGetters(['CART'])
  },
  mounted () {
    console.log('hello Im here!')
  }
}
</script>

<style>
.v-main-wrapper {
    max-width: 900px;
    margin: 0 auto;
    color: #4e4b4b;
}
</style>
