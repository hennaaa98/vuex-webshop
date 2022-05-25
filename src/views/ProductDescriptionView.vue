<template>
  <div class="productdescription">
    <ProductDescription 
    :product="getProduct()" />
  </div>
</template>

<script>
import ProductDescription from '../components/products/ProductDescription.vue'
import items from '../data/items.js'

export default {
  name: 'ProductDescriptionView',
  components: {
    ProductDescription
  },
  methods: {
    getProduct() {
      let id = this.$route.params.id
      return items.find(product => product.id == id)
    }
  }
}

</script>