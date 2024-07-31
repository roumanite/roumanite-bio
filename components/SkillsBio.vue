<template>
  <section class="p-12">
    <h2 class="text-4xl mb-4">Skills</h2>
    <div class="mb-4 border-b border-gray-200 dark:border-gray-700">
      <ul class="flex flex-wrap -mb-px text-sm font-medium text-center"
        id="default-tab"
        data-tabs-toggle="#default-tab-content"
        role="tablist"
        data-tabs-active-classes="text-white bg-blue-600 rounded-lg active"
        
      >
        <li class="me-2" role="presentation">
          <button
          class="inline-block px-4 py-3"
          id="all-tab" data-tabs-target="#all" type="button" role="tab" aria-controls="all" aria-selected="false">
            All
          </button>
        </li>
        <li class="me-2" role="presentation">
          <button
          class="inline-block px-4 py-3"
          id="backend-frameworks-tab" data-tabs-target="#backend-frameworks" type="button" role="tab" aria-controls="backend-frameworks" aria-selected="false">
            Backend Frameworks
          </button>
        </li>
        <li class="me-2" role="presentation">
          <button
          class="inline-block px-4 py-3"
          id="frontend-frameworks-tab" data-tabs-target="#frontend-frameworks" type="button" role="tab" aria-controls="frontend-frameworks" aria-selected="false">
            Frontend Frameworks
          </button>
        </li>
        <li role="presentation">
          <button
          class="inline-block px-4 py-3"
          id="cloud-tab" data-tabs-target="#cloud" type="button" role="tab" aria-controls="cloud" aria-selected="false">
            Cloud
          </button>
        </li>
      </ul>
    </div>
    <div id="default-tab-content">
      <div class="hidden" id="all" role="tabpanel" aria-labelledby="all-tab">
        <div class="flex gap-4 items-start">
          <img class="h-20" v-for="language in languages" :src="language">
        </div>
      </div>
      <div class="hidden" id="backend-frameworks" role="tabpanel" aria-labelledby="backend-frameworks-tab">
        <img class="h-24" v-for="framework in backendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="frontend-frameworks" role="tabpanel" aria-labelledby="frontend-frameworks-tab">
        <img class="h-24" v-for="framework in frontendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="cloud" role="tabpanel" aria-labelledby="cloud-tab">
        <img class="h-24" v-for="cloudService in cloud" :src="cloudService">
      </div>
      <div class="hidden" id="etc" role="tabpanel" aria-labelledby="etc-tab">
        <img class="h-24" v-for="service in etc" :src="service">
      </div>
    </div>
  </section>
</template>
<script setup>
  import { onMounted } from 'vue'
  import { useFlowbite } from '~/composables/useFlowbite';
  import { initFlowbite } from 'flowbite'

  onMounted(() => {
      useFlowbite(() => {
          initFlowbite();
      })
  })

  const languages = ['ruby.png', 'golang.png', 'java.png', 'javascript.png']
  const backendFrameworks = ['rails.png', 'spring.png']
  const frontendFrameworks = ['react.png', 'reactnative.png']
  const cloud = ['aws.png', 'kubernetes.png']
  const etc = ['rabbitmq.png']
</script>