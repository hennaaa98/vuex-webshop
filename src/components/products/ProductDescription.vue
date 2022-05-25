<template>
  <div class="single-item">
    <div v-if="product" class="single-item-card">
      <img v-bind:src="product.image" class="single-item-image" />

      <div class="single-item-information">
        <div class="single-item-details">
          <p class="single-item-title">{{ product.name }}</p>
        </div>

        <p class="single-item-description">{{ product.description }}</p>
        <p class="single-item-price">${{ product.price.toFixed(2) }}</p>

        <div class="button-container">
          <button class="single-item-add" @click="addToCart()">Add To Cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['product'],
    methods: {
      addToCart() {
        this.$store.commit('addToCart', this.product)
      }
    },
    computed: {
      product_total() {
        return this.$store.getters.productQuantity(this.product)
      }
    }
  }
</script>

<style lang="css">
  .single-item-card {
    width: 60%;
    margin: 2rem auto;
    display: flex;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
  }

  .single-item-image {
    width: 60%;
    object-fit: contain;
    margin-right: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
  }

  .single-item-information {
    padding: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    color: #333;
    text-align: left;
  }

  .single-item-title {
    font-size: 1.5rem;
    font-weight: bold;
  }

  p {
    margin: 0;
  }

  .single-item-description {
    font-size: 1rem;
  }

  .single-item-price {
    font-size: 1.5rem;
    font-weight: bold;
  }

  .single-item-add {
    width: 100%;
    padding: 10px 17px;
    background: #42b883;
    color: #eeeeee;
    border: 1px solid #42b883;
    border-radius: 10px;
    font-size: 1.2rem;
    font-weight: bold;
    cursor: pointer;
    outline: none;
  }
</style>