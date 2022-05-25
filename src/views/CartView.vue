<template>
  <div class="cart">
    <div class="cart-items">
    <CartItemCard
      v-for="product in products"
      :key="product.id"
      :product="product" />
    </div>

    <div class="cart-summary">
      <CartSummaryPaymentCard />
    </div>

  </div>
</template>

<script>
import CartItemCard from '../components/cart/CartItemCard.vue'
import CartSummaryPaymentCard from '../components/cart/CartSummaryPaymentCard.vue'

  export default {
    components: {
      CartItemCard,
      CartSummaryPaymentCard
    },
    computed: {
      products() {
        console.log(this.$store.getters.cartItems);
        return this.$store.getters.cartItems
      }
    }
  }
</script>

<style lang="css">
  .cart {
    margin: 2rem auto;
    width: 1100px;
    display: flex;
    justify-content: space-between;
  }

  .cart-items {
    flex: 0.7 1;
    margin-right: 1rem;
  }

  .cart-summary {
    height: 200px;
    flex: 0.3 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
  }
</style>