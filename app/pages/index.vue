<script lang="ts" setup>
useSeoMeta({
  title: 'Home | Zakky Pusponegoro',
  description: 'Portfolio pribadi Muhammad Zakky Pusponegoro',
});

const contact = () => {
  window.location.href = "mailto:emailkamu@gmail.com";
};
</script>

<template>
  <section class="min-h-screen bg-[#f8f6ee] flex items-center justify-center px-6 md:px-12">
    <div class="max-w-7xl w-full grid md:grid-cols-2 mt-40 mb-10 gap-12 items-center">
      <div class="space-y-6">
        <p class="text-lg font-semibold tracking-wide text-gray-700 fade-up">Halo! Saya</p>
        <h1 class="text-4xl md:text-6xl xl:text-7xl font-black leading-tight tracking-wide fade-up delay-100">
          MUHAMMAD <br />
          ZAKKY <br />
          PUSPONEGORO
        </h1>
        <p class="text-lg md:text-xl text-gray-600 max-w-lg leading-relaxed fade-up delay-200">
          Seorang <i>fresh graduate</i> dari SMAN 1 Mejayan yang tertarik di bidang <b>kreatif</b> dan <b>kepenulisan</b>.
          Saya senang membuat karya visual, cerita, dan ide yang bermakna.
        </p>
        <div class="flex gap-4 flex-wrap fade-up delay-300">
          <button @click="contact" class="bg-[#1a1b27] text-white px-8 py-3 rounded-full font-semibold shadow-lg hover:shadow-xl hover:-translate-y-1 transition duration-300">
            Hubungi Saya
          </button>
          <a href="/cv.pdf" download>
            <button class="border-2 border-[#1a1b27] text-[#1a1b27] px-8 py-3 rounded-full font-semibold hover:bg-[#1a1b27] hover:text-white transition duration-300">
              Download CV
            </button>
          </a>
        </div>
      </div>
      <div class="fade-up delay-200">
        <div class="rounded-[2.5rem] overflow-hidden shadow-2xl hover:scale-[1.02] transition duration-500">
          <img src="/images/foto-aku.png" alt="profile" class="w-full h-112.5 md:h-150 object-cover" />
        </div>
      </div>
    </div>
  </section>
</template>
