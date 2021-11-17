<template>
  <div id="app">
    <header>
      <img src="./assets/spotify-logo.png" alt="spotify logo">
    </header>
    <CardsContainer></CardsContainer>
  </div>
</template>

<script>
import CardsContainer from './components/CardsContainer.vue'

export default {
  name: 'App',
  components: {
    CardsContainer
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
@import 'styles/main';
</style>
