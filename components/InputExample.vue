<script setup lang="ts">
const props = defineProps({
  label: {
    type: String,
    required: true,
  },
  value: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="flex flex-col gap-1">
    <label class="text-sm font-medium">{{ label }}</label>
    <input :value="value" class="p-1 rounded-md" />
  </div>
</template>
