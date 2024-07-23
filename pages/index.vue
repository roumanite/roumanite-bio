<template>
  <div>
    <section class="bg-white dark:bg-gray-900">
      <div class="flex py-8 px-4 mx-auto w-fit text-center lg:py-16">
        <img class="rounded-full w-36 h-36" src="/assets/avatar.png" alt="Extra large avatar">
        <div class="">
          <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
            Hello World!
          </h1>
          <p class="mb-8 text-lg font-normal text-gray-500 lg:text-xl px-16 dark:text-gray-400">
            Explore the pages below to learn more about me
          </p>
        </div>
      </div>
      <div>
        <NuxtLink to="/bio">
          Bio
        </NuxtLink>
        <NuxtLink to="/projects">
          Projects
        </NuxtLink>
        <NuxtLink to="/blog">
          Blog
        </NuxtLink>
      </div>
    </section>
  </div>
</template>
