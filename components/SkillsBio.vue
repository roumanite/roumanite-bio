<template>
  <section class="p-12">
    <h2 class="text-4xl mb-4">Skills</h2>
    <div class="mb-4 border-b border-gray-200 dark:border-gray-700">
      <ul class="flex flex-wrap -mb-px text-sm font-medium text-center"
        id="default-tab"
        data-tabs-toggle="#default-tab-content"
        role="tablist"
        data-tabs-active-classes="border-white border-4 rounded-lg active"
      >
        <TabButton id="all">
          All
        </TabButton>
        <TabButton id="backend-frameworks">
          Backend Frameworks
        </TabButton>
        <TabButton id="frontend-frameworks">
          Frontend Frameworks
        </TabButton>
        <TabButton id="cloud">
          Cloud
        </TabButton>
      </ul>
    </div>
    <div id="default-tab-content">
      <div class="hidden" id="all" role="tabpanel" aria-labelledby="all-tab">
        <div class="flex gap-4 items-start">
          <img class="h-20" v-for="language in languages" :src="language">
        </div>
      </div>
      <div class="hidden" id="backend-frameworks" role="tabpanel" aria-labelledby="backend-frameworks-tab">
        <img class="h-20" v-for="framework in backendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="frontend-frameworks" role="tabpanel" aria-labelledby="frontend-frameworks-tab">
        <img class="h-20" v-for="framework in frontendFrameworks" :src="framework">
      </div>
      <div class="hidden" id="cloud" role="tabpanel" aria-labelledby="cloud-tab">
        <img class="h-20" v-for="cloudService in cloud" :src="cloudService">
      </div>
      <div class="hidden" id="etc" role="tabpanel" aria-labelledby="etc-tab">
        <img class="h-20" v-for="service in etc" :src="service">
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