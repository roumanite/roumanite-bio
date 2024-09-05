<template>
  <li class="me-2" role="presentation">
    <button
      class="inline-block px-4 py-3"
      :id="`${id}-tab`"
      :data-tabs-target="`#${id}`"
      type="button"
      role="tab"
      :aria-controls="id"
      aria-selected="false"
    >
      <slot></slot>
    </button>
  </li>
</template>
<script setup>
  const { id } = defineProps({
    id: String
  })
</script>