<script lang="ts" setup>
  useSeoMeta({
    title: 'Home Page',
    description: 'Welcome to the home page of our application.',
  });
</script>

<template>
  <main aria-label="Hero-Section" class="text-[#98A1C4]">
    <div class="min-h-screen flex flex-col justify-end">
      <div class="flex flex-col md:mt-0 mt-52 md:flex-row mx-8 items-center justify-center md:justify-around">
        <div class="space-y-4 md:text-start text-center animate-fade-in">
          <h2 class="font-paragraph text-xl">
            Be The One with World!
          </h2>
          <h1 class="py-4 font-paragraph border-b-2 group cursor-default">
            <span class="text-3xl">Hello, I'm</span><br>
            <span class="text-3xl transition-all duration-300 group-hover:tracking-widest group-hover:text-black">
              Muhammad Zakky Pusponegoro
            </span>
          </h1>

          <div class="flex md:justify-start justify-center gap-4 pt-2 text-sm">
            <a href="https://github.com/NiazTy" target="_blank" class="relative after:absolute after:left-0 after:-bottom-1 after:h-px after:w-0 after:bg-current after:transition-all after:duration-300 hover:after:w-full">~GitHub</a>
            <a href="https://www.instagram.com/m.niazyk" target="_blank" class="relative after:absolute after:left-0 after:-bottom-1 after:h-px after:w-0 after:bg-current after:transition-all after:duration-300 hover:after:w-full">~Instagram</a>
            <a href="https://www.linkedin.com/in/muhammad-zakky-pusponegoro-ab6579287/" target="_blank" class="relative after:absolute after:left-0 after:-bottom-1 after:h-px after:w-0 after:bg-current after:transition-all after:duration-300 hover:after:w-full">~LinkedIn</a>
          </div>
          <p class="font-paragraph text-sm max-w-md">
            A high school student who is passionate about technology, programming, and web development. Always eager to learn and explore new things in the tech world.
          </p>
        </div>
        <div>
          <img
            src="https://niaz.my.id/public/asset/ezgif-6-709821b3dc.gif"
            alt="Profile Picture"
            class=""
          />
        </div>
      </div>
    </div>
    <div class="md:absolute hidden bottom-6 left-1/2 -translate-x-1/2 animate-bounce text-sm opacity-70">
      <a href="#interests">Scroll ↓</a>
    </div>
  </main>
  <section id="interests" aria-label="Interests and Projects" class="min-h-screen bg-[#98A1C4] px-8 text-white animate-fade-in flex flex-col justify-center">
    <div class="my-16 space-y-12 max-w-6xl mx-auto">
      <div class="text-center space-y-2">
        <h2 class="font-paragraph text-2xl">
          Things I Love Exploring
        </h2>
        <p class="text-sm opacity-80">
          Hover around — each interest has its own story.
        </p>
      </div>
      <AppLayoutCardsProject />
    </div>
  </section>
  <AppLayoutCardsContact />
</template>