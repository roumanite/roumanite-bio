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
  <client-only>
    <SkillsBio />
  </client-only>
  <WorkExperienceBio />
  <section class="p-12">
    <h2 class="text-4xl mb-4">Education</h2>
    <ul>
      <li>Murdoch University, Singapore</li>
      <li>Kaplan Diploma in Information Technology, Singapore</li>
    </ul>
  </section>
  <section class="p-12">
    <h2 class="text-4xl mb-4">Awards/Certifications</h2>
    <ul>
      <li>AWS Solutions Architect Associate (SAA-C03)</li>
      <li>Academic Merit Scholarship Award</li>
      <li>Full Kaplan Diploma Scholarship</li>
    </ul>
  </section>
  <section class="p-12">
    <h2 class="text-4xl mb-4">Socials</h2>
  </section>
</template>