<template>
    <div class="product">
      <img v-bind:src="product.image" alt="" class="product-image">
      
      <div class="product-details">
        <p class="details-title">{{ product.name }}</p>
        <p class="details-price">${{ product.price.toFixed(2) }}</p>
      </div>

      <div class="product-details">
        <p class="description">{{ description }}</p>
      </div>

      <div class="product-buttons">
        <button class="view-product-button" @click="goToProduct(product)">View Item</button>
        <button class="add view-product-button" @click="addToCart()">Add To Cart</button>
      </div>
    </div>
</template>

<script>

  export default {
    props: ['product'],
    computed: {
      description() {
        console.log(this.product);
        return this.product.description.substring(0, 150)
      }
    },
    methods: {
      goToProduct(product) {
        this.$router.push('/productdescription/'+product.id)
      },
      addToCart() {
        this.$store.commit('addToCart', this.product)
      }
    }
  }
</script>

<style lang="css">
  .card {
    width: 80%;
    margin: 10%;
    padding: 10px;
    border-radius: 5px;
    background-color: white;
    box-shadow: 0 0 5px gray;
  }

  h5.price {
    color: grey;
  }

  p.description {
    font-size: .85rem;
  }

  p.text-muted {
    color: grey;
  }

  .product {
    width: 30%;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
    margin: 2em auto;
  }

  .product-image {
    width: 100%;
    object-fit: contain;
    border-radius: 10px;
  }

  .product-details {
    padding: 1rem;
    display: flex;
    justify-content: space-between;
  }

  .details-title,
  .details-price {
    font-size: 1.2rem;
    font-weight: bold;
    margin: 0;
  }

  .description {
    margin: 0;
    color: #000;
  }

  .product-buttons {
    display: flex;
    justify-content: space-around;
    flex-direction: column;
    padding: 1rem;
  }

  .view-product-button {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #333333;
    border-radius: 10px;
    font-size: 0.8rem;
    font-weight: bold;
    cursor: pointer;
    margin: .5em 0;
  }

  .add {
    background: #42b883;
    color: white;
    border-color: #42b883;
  }
</style>