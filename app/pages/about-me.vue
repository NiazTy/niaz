<script lang="ts" setup>
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

const timeline = [
  {
    year: "Awal SMA",
    title: "Realita Sekolah",
    text: "SMA nggak seindah film. Lebih banyak filler episode, tapi justru di situ aku belajar bertahan dan menerima realita.",
    img: "/images/photograph/IMG_0056.webp",
    icon: GraduationCap,
  },
  {
    year: "Prestasi",
    title: "Tetap Berusaha",
    text: "Walaupun terasa biasa saja, aku tetap fokus belajar dan berprestasi supaya waktuku nggak terbuang sia-sia.",
    img: "/images/photograph/IMG_0056.webp",
    icon: BookOpen,
  },
  {
    year: "Kenal Komputer",
    title: "Logika & Teknologi",
    text: "Mulai kenal dunia komputer dan logika. Capek, tapi di sinilah aku belajar berpikir sistematis dan problem solving.",
    img: "/images/photograph/IMG_0056.webp",
    icon: Cpu,
  },
  {
    year: "Hobi & Inspirasi",
    title: "Musik, Film, & Cerita",
    text: "J-Pop, anime, film, series — semuanya jadi sumber inspirasi buat ide, cerita, dan karya kreatifku.",
    img: "/images/photograph/IMG_0056.webp",
    icon: Music,
  },
];

const activities = [
  {
    title: "Menulis",
    desc: "Menuangkan ide menjadi cerita, puisi, dan naskah film pendek.",
    icon: PenTool,
    size: "big",
  },
  {
    title: "Film & Visual",
    desc: "Membuat film pendek, sinematografi, dan editing visual.",
    icon: Film,
    size: "tall",
  },
  {
    title: "Programming",
    desc: "Membangun website interaktif dan eksplorasi logika komputer.",
    icon: Cpu,
    size: "normal",
  },
  {
    title: "Ide Kreatif",
    desc: "Mengembangkan konsep, storytelling, dan problem solving.",
    icon: GraduationCap,
    size: "normal",
  },
];


const audioRef = ref<HTMLAudioElement | null>(null);
const playing = ref(false);

const firstInteraction = () => {
  if (!audioRef.value) return;
  audioRef.value.volume = 0.4;
  audioRef.value.play().catch(() => {});
  playing.value = true;
  window.removeEventListener("scroll", firstInteraction);
};

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

const revealEls = ref<Element[]>([]);
const registerReveal = (el: Element | ComponentPublicInstance | null) => {
  if (el instanceof Element) revealEls.value.push(el);
};

const sectionRef = ref<HTMLElement | null>(null);
const lineHeight = ref(0);
let observer: IntersectionObserver;

onMounted(() => {
  const revealObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("show");
        }
      });
    },
    { threshold: 0.2 }
  );
  revealEls.value.forEach((el) => revealObserver.observe(el));

  const handleScroll = () => {
    if (!sectionRef.value) return;
    const rect = sectionRef.value.getBoundingClientRect();
    const windowHeight = window.innerHeight;
    const progress = Math.min(1, Math.max(0, (windowHeight - rect.top) / rect.height));
    lineHeight.value = progress * 100;
  };

  window.addEventListener("scroll", handleScroll);
  window.addEventListener("scroll", firstInteraction, { once: true });

  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry && entry.isIntersecting && audioRef.value) {
        audioRef.value.play().catch(() => {});
      }
    },
    { threshold: 0.4 }
  );

  if (sectionRef.value) observer.observe(sectionRef.value);

  onUnmounted(() => {
    window.removeEventListener("scroll", handleScroll);
    observer.disconnect();
  });
});
</script>

<template>
  <section
    id="about"
    ref="sectionRef"
    class="bg-[#f8f6ee] py-28 px-6 md:px-12 relative overflow-hidden"
  >
    <audio ref="audioRef" src="/audios/sound.mp3" loop preload="auto" />
    <button
      @click="toggleSound"
      class="fixed bottom-6 right-6 z-50 bg-[#1a1b27] text-white p-3 rounded-full shadow-lg"
    >
      <component :is="playing ? Volume2 : VolumeX" class="w-5 h-5" />
    </button>
    <div class="max-w-6xl mx-auto">
      <div class="text-center mb-20">
        <h2 class="text-4xl font-black tracking-widest">MY JOURNEY</h2>
      </div>
      <div class="max-w-3xl mx-auto text-center text-gray-600 leading-relaxed mb-24">
        <p>
          Halo, saya <b>Muhammad Zakky Pusponegoro</b>, di dunia maya dikenal
          sebagai <b>Niaz</b>. Seorang pelajar yang menikmati hidup
          sebagai panggung sandiwara — dijalani saja, bahkan saat jatuh.
        </p>
      </div>
      <div class="relative">
        <div class="absolute left-1/2 top-0 w-0.5 h-full bg-gray-200 -translate-x-1/2" />
        <div
          class="absolute left-1/2 top-0 w-0.5 bg-[#1a1b27] -translate-x-1/2 transition-all duration-200"
          :style="{ height: lineHeight + '%' }"
        />
        <div class="space-y-24">
          <div
            v-for="(item, i) in timeline"
            :key="item.title"
            :ref="registerReveal"
            class="reveal grid md:grid-cols-2 gap-10 items-center"
            :class="i % 2 === 0 ? 'reveal-left' : 'reveal-right'"
          >
            <div :class="i % 2 === 0 ? 'md:text-right md:pr-12' : 'md:order-2 md:text-left md:pl-12'">
              <p class="text-sm text-gray-400 mb-2">{{ item.year }}</p>
              <h3 class="text-xl font-semibold mb-3">{{ item.title }}</h3>
              <p class="text-gray-600">{{ item.text }}</p>
            </div>
            <div :class="i % 2 === 0 ? '' : 'md:order-1'">
              <div class="rounded-2xl overflow-hidden shadow-xl hover:scale-[1.03] transition duration-500">
                <img :src="item.img" class="w-full h-64 object-cover" />
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-36">
        <h3 class="text-3xl font-bold text-center mb-16 tracking-wide">
          What I Do
        </h3>
        <div class="grid grid-cols-1 md:grid-cols-3 auto-rows-[180px] gap-6">
          <div
            v-for="(act, i) in activities"
            :key="act.title"
            :ref="registerReveal"
            class="bento reveal group relative rounded-3xl bg-white shadow-xl overflow-hidden cursor-pointer p-8 flex flex-col justify-between"
            :class="{
              'md:col-span-2 md:row-span-2': act.size === 'big',
              'md:row-span-2': act.size === 'tall'
            }"
            :style="{ transitionDelay: i * 120 + 'ms' }"
          >
            <component :is="act.icon" class="w-10 h-10 text-[#1a1b27]" />
            <div>
              <h4 class="text-xl font-semibold mb-2">{{ act.title }}</h4>
              <p class="text-gray-600 text-sm opacity-0 translate-y-4 group-hover:opacity-100 group-hover:translate-y-0 transition duration-300">
                {{ act.desc }}
              </p>
            </div>
            <div class="absolute inset-0 bg-[#1a1b27]/5 opacity-0 group-hover:opacity-100 transition" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
