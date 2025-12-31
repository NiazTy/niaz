<script lang="ts" setup>
  useSeoMeta({
    title: 'Home Page',
    description: 'Welcome to the home page of our application.',
  });
  const active = ref<'web' | 'programming' | 'writing'>('web')

  const projects = {
    web: {
      title: 'Personal Portfolio Website',
      desc: 'A minimalist and interactive portfolio built with Nuxt & Tailwind.',
      link: '#'
    },
    programming: {
      title: 'Problem Solving Playground',
      desc: 'Small experiments and scripts to sharpen logic and algorithmic thinking.',
      link: '#'
    },
    writing: {
      title: 'Technical Notes & Blogs',
      desc: 'Writing about what I learn, struggle with, and finally understand.',
      link: '#'
    }
  }
</script>
<template>
  <div class="hidden lg:grid grid-cols-1 md:grid-cols-3 gap-6">
    <div @mouseenter="active = 'web'" :class="active === 'web' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Web Development
      </h3>
      <p class="text-sm">
        Turning ideas into interactive web experiences.
      </p>
    </div>
    <div @mouseenter="active = 'programming'" :class="active === 'programming' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Programming
      </h3>
      <p class="text-sm">
        Playing with logic, patterns, and problem solving.
      </p>
    </div>
    <div @mouseenter="active = 'writing'" :class="active === 'writing' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Writing
      </h3>
      <p class="text-sm">
        Documenting thoughts, ideas, and lessons learned.
      </p>
    </div>
  </div>
  <!-- Mobile Version & Tablet -->
  <div class="grid lg:hidden grid-cols-1 md:grid-cols-3 gap-6">
    <div @click="active = 'web'" :class="active === 'web' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Web Development
      </h3>
      <p class="text-sm">
        Turning ideas into interactive web experiences.
      </p>
    </div>
    <div @click="active = 'programming'" :class="active === 'programming' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Programming
      </h3>
      <p class="text-sm">
        Playing with logic, patterns, and problem solving.
      </p>
    </div>
    <div @click="active = 'writing'" :class="active === 'writing' ? 'border-white shadow-xl' : 'border-gray-300 opacity-70'" class="group cursor-pointer p-6 border rounded-xl transition-all duration-300 hover:-translate-y-2 hover:opacity-100">
      <h3 class="font-paragraph text-xl mb-2">
        Writing
      </h3>
      <p class="text-sm">
        Documenting thoughts, ideas, and lessons learned.
      </p>
    </div>
  </div>
  <div class="relative p-8 border text-[#98A1C4] rounded-2xl transition-all duration-500 bg-white backdrop-blur">
      <span class="text-xs font-bold uppercase tracking-widest opacity-70">
        Featured Project
      </span>
      <h4 class="font-paragraph text-xl mt-2">
        {{ projects[active].title }}
      </h4>
      <p class="text-sm opacity-80 mt-2 max-w-xl">
        {{ projects[active].desc }}
      </p>
      <a :href="projects[active].link" class="inline-block mt-4 text-sm underline hover:text-black transition">
        View Project →
      </a>
    </div>
</template>