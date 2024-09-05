<template>
  <section class="p-12">
    <h2 class="text-4xl mb-4">Work Experience</h2>
    <ol class="sm:flex">
      <li class="relative mb-6 sm:mb-0" v-for="experience in experiences">
        <TimelineHeader />
        <div class="mt-3 sm:pe-8">
          <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{ experience.name }}</h3>
          <time class="block mb-2 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{{ experience.date }}</time>
          <section>
            <ul>
              <li v-for="point in experience.points">{{ point }}</li>
            </ul>
          </section>
        </div>
      </li>
    </ol>
  </section>
</template>
<script setup>
  const experiences = [
    {
      name: 'VersaFleet',
      date: 'October 2019 - April 2022',
      points: [
        'Maintain legacy monolithic application that solves vehicle routing problem and provides a command center for brand owners and transporters.',
        'Communicate with customer experience team to understand the problems any client was facing and solve the bugs by gathering more hints through Sentry and Datadog',
        'Stack: Ruby on Rails, PostgreSQL, Redis, React, Redux, React Native'
      ]
    },
    {
      name: 'GotSurge',
      date: 'October 2019 - April 2022',
      points: [
        'Job description'
      ]
    },
    {
      name: 'Sephora SEA',
      date: 'April 2022 - present',
      points: [
        'Job description'
      ]
    }
  ]
</script>