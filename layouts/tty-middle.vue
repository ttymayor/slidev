<script setup lang="ts">
import Footer from "../components/Footer.vue";
</script>

<template>
  <div class="slidev-layout tty-middle">
    <div class="flex flex-col items-center justify-center">
      <slot />
    </div>
  </div>
  <Footer />
</template>

<style>
.slidev-layout.tty-middle {
  @apply flex flex-col items-center justify-center;
}
</style>
