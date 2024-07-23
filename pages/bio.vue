<template>
  <section>
    <div class="p-16">
      <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
        Hi! I'm Grace Ariel.
      </h1>
      <p>
        I'm a software engineer specializing in web development.
      </p>
    </div>
  </section>
  <section>
    <img class="w-36" v-for="language in languages" :src="language">
    <img class="w-36" v-for="framework in backendFrameworks" :src="framework">
    <img class="w-36" v-for="cloudService in cloud" :src="cloudService">
  </section>
</template>
<script setup>
  const languages = ['golang.png']
  const backendFrameworks = ['rails.png', 'spring.png']
  const cloud = ['aws.png']
</script>