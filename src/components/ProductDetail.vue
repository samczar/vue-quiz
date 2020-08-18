<template>
  <div class="productDetail">
    <div>
      <h4>Product Detail</h4>
      <form>
        Name:
        <input type="text" v-model="productDetails.name" />
        <br />Year Of Production:
        <input type="text" v-model="productDetails.expireDate" />
        <br />Expiry Date:
        <input type="text" v-model="productDetails.yearOfProduction" />
        <button @click.prevent="save">Save</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'productDetail',
  props: ['product'],
  data() {
    return {
      productDetails: { ...this.product },
    }
  },
  methods: {
    save() {
      this.$emit('saveProduct', this.product = this.productDetails)
    }
  },
  watch: {
    productDetails(oldval, newval) {
      this.productDetails = { ...this.product }
    }
  }
}
</script>

<style>
</style>