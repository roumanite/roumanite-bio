<template>
  <section class="px-16 pb-10">
    <h2 class="text-4xl mb-4">Skills</h2>
    <div class="mb-4">
      <ul class="flex flex-wrap -mb-px text-sm font-medium text-center"
        id="default-tab"
        data-tabs-toggle="#default-tab-content"
        role="tablist"
        data-tabs-active-classes="border-white border-4 rounded-lg active"
      >
        <TabButton id="all">
          All
        </TabButton>
        <TabButton id="languages">
          Languages
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
      <TabContent id="all">
        <div v-for="group in all" class="mb-8 flex gap-4 items-center">
          <img
            :class="`h-${item.size}`"
            v-for="item in group"
            :src="item.name"
          >
        </div>
      </TabContent>
      <TabContent id="languages">
        <div class="flex gap-4 items-center">
          <img
            :class="`h-${language.size}`"
            v-for="language in languages"
            :src="language.name"
          >
        </div>
      </TabContent>
      <TabContent id="backend-frameworks">
        <div class="flex gap-4 items-center">
          <img
            :class="`h-${framework.size}`"
            v-for="framework in backendFrameworks"
            :src="framework.name"
          >
        </div>
      </TabContent>
      <TabContent id="frontend-frameworks">
        <div class="flex gap-4 items-center">
          <img
            :class="`h-${framework.size}`"
            v-for="framework in frontendFrameworks"
            :src="framework.name"
          >
        </div>
      </TabContent>
      <TabContent id="cloud">
        <div class="flex gap-4 items-center">
          <img
            :class="`h-${cloudService.size}`"
            v-for="cloudService in cloud"
            :src="cloudService.name"
          >
        </div>
      </TabContent>
      <TabContent id="etc">
        <div class="flex gap-4 items-center">
          <img
            :class="`h-${service.size}`"
            v-for="service in etc"
            :src="service.name"
          >
        </div>
      </TabContent>
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

  const languages = [
    { name: 'ruby.png', size: 20 },
    { name: 'golang.png', size: 12 },
    { name: 'java.png', size: 20 },
    { name: 'javascript.png', size: 20 }
  ]
  const backendFrameworks = [
    { name: 'rails.png', size: 14 },
    { name: 'spring.png', size: 12 }
  ]
  const frontendFrameworks = [
    { name: 'react.png', size: 12 },
    { name: 'reactnative.png', size: 12 }
  ]
  const cloud = [
    { name: 'aws.png', size: 12 },
    { name: 'kubernetes.png', size: 12 }
  ]
  const etc = [
    { name: 'rabbitmq.png', size: 12 }
  ]
  const all = [languages, backendFrameworks, frontendFrameworks, cloud, etc]
</script>