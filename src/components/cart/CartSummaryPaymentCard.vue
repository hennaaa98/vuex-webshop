<template>
  <h4 class="summary-title">Cart Summary</h4>
  <div class="summary-price">
    <span>Subtotal:</span>
    <span>${{ cart_total.toFixed(2) }}</span>
  </div>
  <div class="summary-price">
    <span>Items qty:</span>
    <span>{{ totalCartQuantity }}</span>
  </div>
  <button class="summary-checkoutBtn">
    <span>Total ${{ cart_total.toFixed(2) }}</span>
  </button>
</template>

<script>
 export default {
    props: ['product'],
    computed: {
      item_cost() {
        return this.product.price * this.product.quantity
      },
      cart_total() {
        return this.$store.getters.cartTotal
      },
      totalCartQuantity() {
        return this.$store.getters.totalCartQuantity
      }
    }
  }
</script>

<style lang="css">
  .summary-title {
    font-size: 1.2rem;
    font-weight: bold;
    margin: 0;
  }

  .summary-price {
    display: flex;
    align-items: center;
  }

  .summary-price span:nth-child(1) {
    font-size: 0.9rem;
    flex: 0.6;
  }

  .summary-price span:nth-child(2) {
    flex: 0.4;
    font-size: 1.2rem;
    font-weight: bold;
  }

  .summary-checkoutBtn {
    padding: 10px 17px;
    border: 1px solid #42b883;
    border-radius: 10px;
    background: #42b883;
    color: #eeeeee;
    font-size: 1.2rem;
    font-weight: bold;
    cursor: pointer;
  }

  .summary-checkoutBtn:hover {
    opacity: 0.75;
  }
</style>