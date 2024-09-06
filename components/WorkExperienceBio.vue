<template>
  <section class="px-16 pb-8">
    <h2 class="text-4xl mb-4">Work Experience</h2>
    <Timeline :events="experiences" />
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
        'Develop microservices for runsheet management and driver broadcasting.',
        'Stack: Ruby on Rails, Go-gin, MongoDB, PostgreSQL, Elasticsearch, React, Redux, React Native, TypeScript, ActiveMQ, Kafka, Jenkins, Kubernetes'
      ]
    },
    {
      name: 'Sephora SEA',
      date: 'April 2022 - present',
      points: [
        'Ensure smooth customer shopping journey from browsing products to goods delivery, including refund/order cancellation',
        'Software domain: e-commerce, order management, tracking management, inventory, last mile notification',
        'Stack: Ruby on Rails, Go, Spring, DynamoDB, PostgreSQL, Elasticsearch, React, Redis, RabbitMQ, Kubernetes'
      ]
    }
  ]
</script>