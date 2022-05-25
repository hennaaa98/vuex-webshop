<template>
  <div class="cart-item">
    <img v-bind:src="product.image" class="cart-image" />
    <div class="cart-item-details">
      <p class="details-name">{{ product.name }}</p>
      <p class="details-description">{{ product.description }}</p>
      <p class="cart-details-price">${{ product.price.toFixed(2) }}</p>
      
      <div class="cart-item-actions">
        <div class="cart-item-quantity">
          <label htmlFor="qty">Qty</label>
          <input
            min="1"
            type="number"
            id="qty"
            name="qty"
            v-model.number="qty"
            v-on:change="event => modifyQuantity(event)"
          />
        </div>
        <div class="remove" @click="removeFromCart()">
          <font-awesome-icon :icon="['fa', 'trash']" class="trash-icon" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['product'],
    computed: {
      item_cost() {
        return this.product.price * this.product.quantity
      }
    },
    methods: {
      modifyQuantity(e) {
        console.log(this.product, this.product.image)
        return this.$store.commit('modifyQuantity', {product: this.product, quantity: e.target.value})
      },
      removeFromCart() {
        return this.$store.commit('removeFromCart', this.product)
      }
    },
    data() {
        return {
        qty: this.product.quantity,
        image: this.product.image
      }
    }
  }
</script>

<style lang="css">
  .cart-item {
    margin-bottom: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
    display: flex;
  }

  .cart-image {
    width: 350px;
    object-fit: contain;
    border-radius: 10px;
  }

  .cart-item-details {
    padding: 1rem 3rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    color: #333333;
    width: 100%;
  }

  .details-name {
    font-size: 1.2rem;
    font-weight: bold;
  }

  .details-description {
    font-size: 0.8rem;
  }
  
  .cart-details-price {
    font-size: 1rem;
    font-weight: bold;
  }

  .cart-item-actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .cart-item-quantity {
    display: flex;
    align-items: center;
  }

  .cart-item-quantity input {
    padding: 5px 10px;
    margin-left: 0.4rem;
    width: 33px;
    border-radius: 5px;
    border: 1px solid #333333;
    outline: none;
  }

  .remove {
    cursor: pointer;
    color: #42b883;
    font-size: 1.2em;
  }
</style>