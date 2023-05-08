<script setup>
// import SkeletonLoading from './components/SkeletonLoading.vue'
import SearchEvents from './components/SearchEvents.vue'
import HeaderComp from './components/HeaderComp.vue'
</script>

<template>
  <div class="container mx-auto">
    <HeaderComp />
    <SearchEvents />
  </div>
</template>

<style>
/* loaded local font */
@font-face {
  font-family: 'BRFirma';
  src: local('BRFirma'), url(./assets/font/BRFirma/BRFirma-Regular.ttf) format('truetype');
}

/* use the font throughout the page body*/
body {
  font-family: 'BRFirma';
}
</style>
