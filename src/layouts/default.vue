<template>
      <div>
           <Nav /> 
           <RouterView />
           <Footer />
      </div>
</template>

<style lang="scss" scoped>

</style>

<script setup>
import Nav from '../components/NavComponets.vue'
import Footer from '../components/FooterComponets.vue'
</script>
