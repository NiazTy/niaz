<script lang="ts" setup>
useSeoMeta({
  title: 'About Me - Muhammad Zakky Pusponegoro',
  description: 'Halaman tentang Muhammad Zakky Pusponegoro, seorang pelajar yang tertarik di bidang kreatif dan kepenulisan.'
});

import {
  GraduationCap,
  Cpu,
  Music,
  BookOpen,
  PenTool,
  Film,
  Volume2,
  VolumeX,
} from "lucide-vue-next";

/* ================= DATA ================= */

const timeline = [
  {
    year: "Awal SMA",
    title: "Realita Sekolah",
    text: "SMA nggak seindah film. Lebih banyak filler episode, tapi justru di situ aku belajar bertahan dan menerima realita.",
    img: "/images/aku-sma.webp",
  },
  {
    year: "Prestasi",
    title: "Tetap Berusaha",
    text: "Walaupun terasa biasa saja, aku tetap fokus belajar dan berprestasi supaya nggak terbuang sia-sia.",
    img: "/images/prestasi-aku.jpg",
  },
  {
    year: "Kerja Sama",
    title: "Bekerja Sama",
    text: "Kerja sama dengan teman-teman di sekolah bikin aku belajar banyak hal baru.",
    img: "/images/kerja-sama.jpg",
  },
  {
    year: "Pengalaman",
    title: "Banyak Hal Terjadi",
    text: "Banyak pengalaman tak terlupakan selama SMA.",
    img: "/images/pengalaman-aku.jpg",
  },
];

const activities = [
  { title: "Menulis", desc: "Cerita & naskah film.", icon: PenTool },
  { title: "Film & Visual", desc: "Sinematografi & editing.", icon: Film },
  { title: "Programming", desc: "Website & eksplorasi logika.", icon: Cpu },
  { title: "Ide Kreatif", desc: "Storytelling & konsep.", icon: GraduationCap },
];

/* ================= AUDIO ================= */

const audioRef = ref<HTMLAudioElement | null>(null);
const playing = ref(false);

const toggleSound = () => {
  if (!audioRef.value) return;
  if (audioRef.value.paused) {
    audioRef.value.play();
    playing.value = true;
  } else {
    audioRef.value.pause();
    playing.value = false;
  }
};

/* ================= TIMELINE LINE ================= */

const sectionRef = ref<HTMLElement | null>(null);
const lineHeight = ref(0);

onMounted(() => {
  const handleScroll = () => {
    if (!sectionRef.value) return;
    const rect = sectionRef.value.getBoundingClientRect();
    const windowHeight = window.innerHeight;
    const progress = Math.min(1, Math.max(0, (windowHeight - rect.top) / rect.height));
    lineHeight.value = progress * 100;
  };
  window.addEventListener("scroll", handleScroll);
});
</script>

<template>
  <!-- ================= HEADER ================= -->
  <section class="bg-[#f8f6ee]">
    <div
      id="header-about"
      class="flex flex-col md:flex-row pt-32 md:pt-52 pb-12 md:pb-16 px-6 md:px-8 lg:px-0 md:justify-around gap-6"
    >
      <div class="flex flex-col">
        <h1 class="text-4xl md:text-6xl font-snpro text-paragraph leading-tight">
          ABOUT ME
        </h1>
        <p class="text-lg md:text-2xl font-snpro text-paragraph">
          MUHAMMAD ZAKKY PUSPONEGORO
        </p>
        <div class="w-24 md:w-1/2 mt-4 border-2 border-paragraph rounded-2xl"></div>
      </div>
    </div>
  </section>

  <!-- ================= INTRO ================= -->
  <section class="bg-[#1a1b27] text-white">
    <div class="px-6 md:px-24 py-16 md:py-24 space-y-10">
      <p class="text-base md:text-lg leading-relaxed">
        Halo, saya Muhammad Zakky Pusponegoro...
      </p>

      <img
        src="/images/ini-aku-yang-capek.jpg"
        class="w-full rounded-3xl shadow-2xl object-cover"
        alt="Ini Aku"
      />

      <div class="space-y-6 text-base md:text-lg leading-relaxed text-white/90">
        <p>Sekolah di SMAN 1 Mejayan bikin aku sadar...</p>
        <p>Dalam hidup, aku selalu pegang satu motto...</p>
        <p>Dulu aku sering ngelakuin hal-hal nggak jelas...</p>
        <p>Aku suka dengerin lagu-lagu J-Pop...</p>
      </div>
    </div>
  </section>

  <!-- ================= TIMELINE ================= -->
  <section
    id="about"
    ref="sectionRef"
    class="bg-[#f8f6ee] py-20 md:py-28 px-6 md:px-12 relative"
  >
    <audio ref="audioRef" src="/audios/sound.mp3" loop preload="auto" />

    <!-- audio button -->
    <button
      @click="toggleSound"
      class="fixed bottom-4 right-4 md:bottom-6 md:right-6 z-50 bg-[#1a1b27] text-white p-2 md:p-3 rounded-full shadow-lg"
    >
      <component :is="playing ? Volume2 : VolumeX" class="w-4 h-4 md:w-5 md:h-5" />
    </button>

    <div class="max-w-6xl mx-auto">

      <h2 class="text-3xl md:text-4xl font-black text-center mb-16">
        MY JOURNEY
      </h2>

      <!-- timeline line (desktop only) -->
      <div class="relative">
        <div class="hidden md:block absolute left-1/2 top-0 w-0.5 h-full bg-gray-300 -translate-x-1/2"></div>
        <div
          class="hidden md:block absolute left-1/2 top-0 w-0.5 bg-[#1a1b27] -translate-x-1/2 transition-all duration-200"
          :style="{ height: lineHeight + '%' }"
        ></div>

        <div class="space-y-20">
          <div
            v-for="(item, i) in timeline"
            :key="item.title"
            class="flex flex-col md:grid md:grid-cols-2 gap-8 items-center"
          >
            <div class="md:text-right md:pr-12">
              <p class="text-sm text-gray-400 mb-2">{{ item.year }}</p>
              <h3 class="text-xl font-semibold mb-2">{{ item.title }}</h3>
              <p class="text-gray-600">{{ item.text }}</p>
            </div>

            <img
              :src="item.img"
              class="w-full h-60 md:h-64 object-cover rounded-2xl shadow-xl"
            />
          </div>
        </div>
      </div>

      <!-- ================= WHAT I DO ================= -->
      <div class="mt-24 md:mt-36">
        <h3 class="text-2xl md:text-3xl font-bold text-center mb-12">
          What I Do
        </h3>

        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
          <div
            v-for="act in activities"
            :key="act.title"
            class="bg-white p-6 md:p-8 rounded-3xl shadow-lg hover:-translate-y-2 hover:shadow-2xl transition"
          >
            <component :is="act.icon" class="w-8 h-8 mb-4 text-[#1a1b27]" />
            <h4 class="text-lg font-semibold mb-2">{{ act.title }}</h4>
            <p class="text-gray-600 text-sm">{{ act.desc }}</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
