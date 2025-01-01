<template>
  <canvas
    :id="id"
    @click="emit('click')"
    @mouseover="emit('mouseover')"
    @mouseleave="emit('mouseleave')"
  >
  </canvas>
  <div
    class="text-abt-me absolute"
    v-show="showOverlay"
    @click="emit('click')"
    @mouseover="emit('mouseover')"
    @mouseleave="emit('mouseleave')"
  >
    <h1 class="text-4xl">
      {{ text }}
    </h1>
  </div>
</template>
<script setup>
  const { id, showOverlay, text } = defineProps({
    id: String,
    showOverlay: Boolean,
    text: String
  })
  const emit = defineEmits(['click', 'mouseover', 'mouseleave']);
</script>