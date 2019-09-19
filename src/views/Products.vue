<template>
  <div class="products">
    <div class="products_filters">
      <select v-model="currentCategory">
        <option :value="null">All</option>
        <option v-for="category in categories" :key="category.id" :value="category.name">{{category.name}}</option>
      </select>
    </div>
    <ul class="products_list">
      <li class="products_listItem" v-for="product in selectedProducts" :key="product.id">
        <span>{{product.name}}</span><br>
        <span>{{product.description}}</span>
        <button :disabled="$store.state.cart.some((item) => item.id === product.id)" class="products_listItemButton" @click="addToCart(product)">Add to cart</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
  name: 'products',
  data() {
    return {
      categories: [
        {
          id: 1,
          name: 'a'
        },
        {
          id: 2,
          name: 'b'
        },
        {
          id: 3,
          name: 'c'
        },
        {
          id: 4,
          name: 'd'
        }
      ],
      products: [
        {
          id: '1',
          name: 'Fish a b',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: ['a', 'b']
        },
        {
          id: '2',
          name: 'Fish a',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: ['a']
        },
        {
          id: '3',
          name: 'Fish null',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: null
        },
        {
          id: '4',
          name: 'Fish b',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: ['b']
        },
        {
          id: '5',
          name: 'Fish a b c',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: ['a', 'b', 'c']
        },
        {
          id: '6',
          name: 'Fish d',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: ['d']
        },
        {
          id: '7',
          name: 'Fish null',
          description: 'tesasdfs sadfadsfas fsadfasfsaf sfasfsaf 234234234 24323423 sdfsdafsaf sasfssafsafsaf',
          price: '1000',
          category: null
        }
      ],
      currentCategory: null
    }
  },
  computed: {
    selectedProducts() {
      return this.currentCategory ? this.products.filter((product) => product.category && product.category.some((category) => category === this.currentCategory)) : this.products
    }
  },
  methods: {
    ...mapMutations({
      addToCart: 'addToCart',
      removeFromCart: 'removeFromCart'
    })
  }
}
</script>
<style lang="scss">
  .products {
    &_list {
      list-style: none;
      display: flex;
      &Item {
        list-style: none;
      }
    }

  }
</style>