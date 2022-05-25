<template>
  <nav>
    <router-link :class="{active: $route.name === 'Home'}" to="/" style="text-decoration: none;">
      <h2 class="navbar-logo">Vue Vuex Webshop</h2>
    </router-link>
    <div class="nav-links">
      <router-link :class="{active: $route.name === 'Home'}" to="/" style="text-decoration: none;">Products</router-link> |
      <router-link :class="{active: $route.name === 'Cart'}" to="/cart" style="text-decoration: none;">Cart</router-link> |
      <router-link :class="{active: $route.name === 'Cart'}" to="/cart" style="text-decoration: none;">Checkout</router-link>
    </div>
    <div class="cart-area">
      <font-awesome-icon :icon="['fa', 'cart-shopping']" class="shopping-cart-icon" />
      <div class="cart-quantity">{{ totalCartQuantity }}</div>
    </div>
  </nav>
  <router-view/>
</template>

<script>
  export default {
    computed: {
      totalCartQuantity() {
        return this.$store.getters.totalCartQuantity
      }
    }
  }
</script>

<style lang="css">
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 1.2rem;
    background: #42b883;
    color: white;
    position: sticky;
    top: 0;
    left: 0;
    height: 78px;
  }

  .navbar-logo {
    font-size: 30px;
    font-weight: bold;
    color: #fff;
    width: 325px;
  }

  nav a {
    color: white;
  }

  nav .nav-links a {
    margin: 0 .7rem;
  }

  nav .shopping-cart-icon {
    font-size: 1.5em;
  }

  nav .cart-area {
    width: 60px;
    border: none;
    border-radius: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem;
    cursor: pointer;
  }

  nav .cart-quantity {
    font-size: 20px;
  }
</style>