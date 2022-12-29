<template>
  <HeaderApp/>
  <BodyApp/>
</template>

<script>
import BodyApp from './components/BodyApp.vue'
import HeaderApp from './components/HeaderApp.vue'
export default {
  name: 'App',
  components: {
    HeaderApp,
    BodyApp,
  }
}
</script>

<style>
#app {
}
</style>
