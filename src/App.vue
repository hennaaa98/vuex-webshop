<template>
  <NavbarComponent />
</template>

<script>
import NavbarComponent from './components/navbar/NavbarComponent.vue'

  export default {
    components: {
    NavbarComponent
    },
    mounted() {
      this.$store.commit('updateCartFromLocalStorage')
    }
  }
</script>

<style lang="css">
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  margin: 0;
  padding: 0;
}
</style>
