<template>
  <ol class="sm:flex">
    <li class="flex-1 relative mb-6 sm:mb-0" v-for="event in events">
      <EventHeader />
      <div class="mt-3 sm:pe-8">
        <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{ event.name }}</h3>
        <time class="block mb-2 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{{ event.date }}</time>
        <section>
          <ul>
            <li v-for="point in event.points">{{ point }}</li>
          </ul>
        </section>
      </div>
    </li>
  </ol>
</template>
<script setup>
  const { events } = defineProps({
    events: Array
  })
</script>