<template>
  <div class="product">
    <ul>
      <li
        class="products"
        v-for="(product, index) in products"
        :key="index"
        @click="selectProduct = {...product}"
      >
        {{product.name}}
        <product-detail
          :product="selectProduct"
          v-if="selectProduct.name === product.name"
          @saveProduct="selectProduct"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import ProductDetail from '../components/ProductDetail'

export default {
  name: 'products',
  components: {
    'product-detail': ProductDetail
  },
  props: ['products']
  ,
  data() {
    return {
      selectProduct: '',
    }
  },
}
</script>

<style scoped>
.product {
  border: 1px solid black;
}
.products {
  margin-bottom: 0.9em;
  margin-top: 0.9em;
  background-color: black;
  margin-left: auto;
  margin-right: auto;
  width: 90%;
  color: white;
  cursor: pointer;
}
</style>>
