<script setup lang="ts">
import Footer from "../components/Footer.vue";
</script>

<template>
  <div class="slidev-layout default">
    <slot />
  </div>
  <Footer />
</template>

<style>
.slidev-layout h2,
.slidev-layout h3,
.slidev-layout h4,
.slidev-layout h5,
.slidev-layout h6 {
  margin-bottom: 1rem;
}
</style>
