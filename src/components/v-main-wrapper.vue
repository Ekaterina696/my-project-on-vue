<template>
    <div class="v-main-wrapper">
        <vCatalog />
        <vCart v-if="CART.length" :cart_data='CART' />
    </div>
</template>

<script>
import vCatalog from './v-catalog.vue'
import vCart from './v-cart.vue'
import { mapGetters } from 'vuex'

export default {
  name: 'v-main-wrapper',
  components: { vCatalog, vCart },
  props: {},
  data () {
    return {}
  },
  computed: {
    ...mapGetters(['CART'])
  },
  methods: {},
  watch: {},
  mounted () {
    console.log('hello Im here!')
  }
}
</script>

<style>
.v-catalog {
    display: flex;
    justify-content: center;
    align-items: center;
    max-width: 900px;
    margin: 0 auto;
}
</style>
