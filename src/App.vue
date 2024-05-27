<template>
  <q-layout view="hHh lpR fFf">
    <Header @toggle-left-drawer="toggleLeftDrawer" @toggle-cart="toggleCart" />

    <Drawer v-model="leftDrawerOpen" />

    <Cart v-model="cartOpen" :cart="cart" @toggle-cart="toggleCart" />

    <q-page-container>
      <ProductList :products="products" @add-to-cart="addToCart" />
    </q-page-container>

    <q-footer elevated class="bg-pink text-white" style="text-align: center;">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>&copy;2024 Nurul Hayana Putri </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Drawer from './components/Sidebar.vue'
import Cart from './components/Card.vue'
import ProductList from './components/ListProduct.vue'

export default {
  name: 'App',
  components: {
    Header,
    Drawer,
    Cart,
    ProductList
  },
  setup() {
    const leftDrawerOpen = ref(false)
    const cartOpen = ref(false)
    const cart = ref([])
    const products = ref([
    ])

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const toggleCart = () => {
      cartOpen.value = !cartOpen.value
    }

    const addToCart = (product) => {
      cart.value.push(product)
    }

    return {
      leftDrawerOpen,
      cartOpen,
      cart,
      products,
      toggleLeftDrawer,
      toggleCart,
      addToCart
    }
  }
}
</script>
