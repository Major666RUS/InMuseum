<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Products</router-link> |
      <router-link v-if="this.$store.state.cart.length > 0" to="/cart">Cart</router-link>
      <span v-else>Нету товаров</span>
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
