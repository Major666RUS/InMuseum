<template>
  <div class="cart">
    <table>
      <tr v-for="product in $store.state.cart" :key="product.id">
        <td>{{product.name}}</td>
        <td>{{product.price}}</td>
        <td><button @click="removeFromCart(product)">Remove from cart</button></td>
      </tr>
    </table>
  </div>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  name: 'cart',
  methods: {
    ...mapMutations({
      removeFromCart: 'removeFromCart'
    })
  }
}
</script>