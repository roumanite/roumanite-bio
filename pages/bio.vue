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
</template>
<script setup>
  const languages = ['ruby.png', 'golang.png', 'java.png', 'javascript.png']
  const backendFrameworks = ['rails.png', 'spring.png']
  const frontendFrameworks = ['react.png', 'reactnative.png']
  const cloud = ['aws.png', 'kubernetes.png']
  const etc = ['rabbitmq.png']
</script>