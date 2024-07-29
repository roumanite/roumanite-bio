<template>
  <section>
    <div class="p-16">
      <h1 class="mb-4 text-4xl tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
        Hi! I'm Grace Ariel.
      </h1>
      <p>
        I'm a software engineer specializing in web development.
      </p>
      <p>
        Download my resume:
      </p>
    </div>
  </section>
  <section class="p-12">
    <h2 class="text-4xl">Skills</h2>
    <div class="mb-4 border-b border-gray-200 dark:border-gray-700">
      <ul class="flex flex-wrap -mb-px text-sm font-medium text-center" id="default-tab" data-tabs-toggle="#default-tab-content" role="tablist">
        <li class="me-2" role="presentation">
          <button class="inline-block p-4 border-b-2 rounded-t-lg" id="all-tab" data-tabs-target="#all" type="button" role="tab" aria-controls="all" aria-selected="false">
            All
          </button>
        </li>
        <li class="me-2" role="presentation">
          <button class="inline-block p-4 border-b-2 rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300" id="backend-frameworks-tab" data-tabs-target="#backend-frameworks" type="button" role="tab" aria-controls="backend-frameworks" aria-selected="false">
            Backend Frameworks
          </button>
        </li>
        <li class="me-2" role="presentation">
          <button class="inline-block p-4 border-b-2 rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300" id="frontend-frameworks-tab" data-tabs-target="#frontend-frameworks" type="button" role="tab" aria-controls="frontend-frameworks" aria-selected="false">
            Frontend Frameworks
          </button>
        </li>
        <li role="presentation">
          <button class="inline-block p-4 border-b-2 rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300" id="cloud-tab" data-tabs-target="#cloud" type="button" role="tab" aria-controls="cloud" aria-selected="false">
            Cloud
          </button>
        </li>
      </ul>
    </div>
    <div id="default-tab-content">
      <div class="hidden" id="all" role="tabpanel" aria-labelledby="all-tab">
        <div class="flex items-start">
          <img class="w-36" v-for="language in languages" :src="language">
        </div>
      </div>
      <div class="hidden" id="backend-frameworks" role="tabpanel" aria-labelledby="backend-frameworks-tab">
        <img class="w-36" v-for="framework in backendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="frontend-frameworks" role="tabpanel" aria-labelledby="frontend-frameworks-tab">
        <img class="w-36" v-for="framework in frontendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="cloud" role="tabpanel" aria-labelledby="cloud-tab">
        <img class="w-36" v-for="cloudService in cloud" :src="cloudService">
      </div>
      <div class="hidden" id="etc" role="tabpanel" aria-labelledby="etc-tab">
        <img class="w-36" v-for="service in etc" :src="service">
      </div>
    </div>
  </section>
  <section class="p-12">
    <h2 class="text-4xl">Work Experience</h2>
    <ol class="items-center sm:flex">
        <li class="relative mb-6 sm:mb-0">
            <div class="flex items-center">
                <div class="z-10 flex items-center justify-center w-6 h-6 bg-blue-100 rounded-full ring-0 ring-white dark:bg-blue-900 sm:ring-8 dark:ring-gray-900 shrink-0">
                    <svg class="w-2.5 h-2.5 text-blue-800 dark:text-blue-300" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                        <path d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"/>
                    </svg>
                </div>
                <div class="hidden sm:flex w-full bg-gray-200 h-0.5 dark:bg-gray-700"></div>
            </div>
            <div class="mt-3 sm:pe-8">
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white">VersaFleet</h3>
                <time class="block mb-2 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">October 2019 - April 2022</time>
                <p class="text-base font-normal text-gray-500 dark:text-gray-400">
                  Job description
                </p>
            </div>
        </li>
        <li class="relative mb-6 sm:mb-0">
            <div class="flex items-center">
                <div class="z-10 flex items-center justify-center w-6 h-6 bg-blue-100 rounded-full ring-0 ring-white dark:bg-blue-900 sm:ring-8 dark:ring-gray-900 shrink-0">
                    <svg class="w-2.5 h-2.5 text-blue-800 dark:text-blue-300" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                        <path d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"/>
                    </svg>
                </div>
                <div class="hidden sm:flex w-full bg-gray-200 h-0.5 dark:bg-gray-700"></div>
            </div>
            <div class="mt-3 sm:pe-8">
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white">GotSurge</h3>
                <time class="block mb-2 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">October 2019 - April 2022</time>
                <p class="text-base font-normal text-gray-500 dark:text-gray-400">
                  Job description
                </p>
            </div>
        </li>
        <li class="relative mb-6 sm:mb-0">
            <div class="flex items-center">
                <div class="z-10 flex items-center justify-center w-6 h-6 bg-blue-100 rounded-full ring-0 ring-white dark:bg-blue-900 sm:ring-8 dark:ring-gray-900 shrink-0">
                    <svg class="w-2.5 h-2.5 text-blue-800 dark:text-blue-300" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                        <path d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"/>
                    </svg>
                </div>
                <div class="hidden sm:flex w-full bg-gray-200 h-0.5 dark:bg-gray-700"></div>
            </div>
            <div class="mt-3 sm:pe-8">
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white">Sephora SEA</h3>
                <time class="block mb-2 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">April 2022 - present</time>
                <p class="text-base font-normal text-gray-500 dark:text-gray-400">
                  Job description
                </p>
            </div>
        </li>
    </ol>
  </section>
  <section>
    <h2 class="text-4xl">Education</h2>
  </section>
  <section>
    <h2 class="text-4xl">Awards/Certifications</h2>
  </section>
  <section>
    <h2 class="text-4xl">Socials</h2>
  </section>
</template>
<style>
  h1, h2 {
    font-family: 'Varela Round';
  }
</style>
<script setup>
  import { onMounted } from 'vue'
  import { useFlowbite } from '~/composables/useFlowbite';
  import { initTabs } from 'flowbite'

  onMounted(() => {
      useFlowbite(() => {
          initTabs();
      })
  })

  const languages = ['ruby.png', 'golang.png', 'java.png', 'javascript.png']
  const backendFrameworks = ['rails.png', 'spring.png']
  const frontendFrameworks = ['react.png', 'reactnative.png']
  const cloud = ['aws.png', 'kubernetes.png']
  const etc = ['rabbitmq.png']
</script>