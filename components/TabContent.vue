<template>
  <div
    class="hidden"
    :id="id"
    role="tabpanel"
    :aria-labelledby="`${id}-tab`"
  >
    <slot></slot>
  </div>
</template>
<script setup>
  const { id } = defineProps({
    id: String
  })
</script>