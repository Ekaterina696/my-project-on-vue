<template>
  <div class="v-catalog">
    <h1>Каталог товаров</h1>
    <router-link :to="{name: 'cart', params: {cart_data:CART}}">
      <div class="v-catalog__link_to_cart">
        <i class="small material-icons">shopping_basket</i>
        {{ CART.length }}
      </div>
    </router-link>
    <div class="v-catalog__list">
      <vCatalogItem v-for="product in PRODUCTS" :key="product.article" :product_data="product" @addToCart="addToCart" />
    </div>
  </div>
</template>

<script>
import vCatalogItem from './v-catalog-item.vue'
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'v-catalog',
  components: {
    vCatalogItem
  },
  computed: {
    ...mapGetters(['PRODUCTS', 'CART'])
  },
  methods: {
    ...mapActions([
      'GET_PRODUCTS_FROM_API', 'ADD_TO_CART'
    ]),
    addToCart (data) {
      this.ADD_TO_CART(data)
    }
  },
  mounted () {
    this.GET_PRODUCTS_FROM_API()
      .then((response) => {
        if (response.data) {
          console.log('Данные пришли')
        }
      })
  }
}
</script>

<style>
.v-catalog,
.v-catalog__list {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: baseline;
}

.v-catalog__link_to_cart {
  top: 10px;
  right: 10px;
  padding: 10px;
}

.material-icons {
  color: black;
}
</style>
