<template>
  <div>
    <section class="dark:bg-gray-900">
      <div class="flex py-8 px-4 mx-auto w-fit text-center lg:py-16">
        <img class="rounded-full w-36 h-36" src="/assets/avatar.png" alt="Extra large avatar">
        <div class="">
          <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
            Hello World!
          </h1>
          <p class="text-lg font-normal text-gray-500 lg:text-xl px-16 dark:text-gray-400">
            You're looking at Grace Ariel's personal website
          </p>
          <p class="mb-8 text-lg font-normal text-gray-500 lg:text-xl px-16 dark:text-gray-400">
            Explore the pages below to learn more about me
          </p>
        </div>
      </div>
      <div class="flex justify-center gap-16">
        <NuxtLink to="/bio">
          <h1 class="mb-4 text-4xl font-bold tracking-tight leading-none text-gray-900 dark:text-white">
            Bio
          </h1>
        </NuxtLink>
        <NuxtLink to="/projects">
          <h1 class="mb-4 text-4xl font-bold tracking-tight leading-none text-gray-900 dark:text-white">
            Projects
          </h1>
        </NuxtLink>
        <!--
        <NuxtLink to="/blog">
          Blog
        </NuxtLink>
        -->
      </div>
    </section>
  </div>
</template>
<script setup>
  definePageMeta({
    layout: false,
  })
</script>