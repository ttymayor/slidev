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
.slidev-layout h2 {
  margin-bottom: 1rem;
}
</style>
